---
title: Intro aux tests
description: Plan de tests, rédaction et implantation (JUnit, tests unitaires et instrumentation)
hide_table_of_contents: true
---

# Intro aux tests (plan de tests, implantation)

<Row>

<Column>

:::danger Avant la séance (2h)

1. Lire la section sur les tests unitaires dans la documentation Kotlin/Gradle.
2. Regarder la vidéo d'introduction aux tests fournie.
3. Relire les recettes sur les tests et sur la structure de projet.

:::

</Column>

<Column>

## Objectifs

- Comprendre pourquoi écrire des tests (qualité, régression, documentation exécutable).
- Savoir rédiger un plan de tests simple pour une fonctionnalité.
- Implémenter des tests unitaires (JUnit) en Kotlin et exécuter la suite.
- Introduction aux tests d'intégration et instrumentation Android.

</Column>

</Row>

## 1. Qu'est-ce qu'un plan de tests ?

Un plan de tests est un document (ou une courte liste) qui décrit les cas de tests à vérifier pour une fonctionnalité.
Il contient typiquement :

- le nom du cas de test,
- l'entrée (données et état initial),
- l'action à effectuer,
- le résultat attendu,
- les critères d'acceptation.

Exemple (création d'un compte) :

- Cas : Courriel invalide
  - Entrée : "utilisateur@"
  - Action : soumettre le formulaire
  - Attendu : message d'erreur "Courriel invalide"

- Cas : Mot de passe trop court
  - Entrée : mot de passe de 3 caractères
  - Attendu : message d'erreur "Mot de passe trop court"

Le plan permet d'identifier les tests automatisés à écrire en priorité.

## 2. Types de tests

- Tests unitaires : tests rapides qui vérifient une fonction ou une classe isolée (JUnit, kotest...).
- Tests d'intégration : vérifient l'interaction entre plusieurs composants (ex : service + DAO).
- Tests d'UI / instrumentation : tests qui s'exécutent sur un device/emulateur (Espresso, Android Test).

## 3. Bonnes pratiques

- Nommer clairement les tests (Given_When_Then ou testNomScenario).
- Tester un seul comportement par test.
- Garder les tests rapides et indépendants.
- Mocker ou isoler les dépendances lourdes (BD, réseau) pour les tests unitaires.

## 4. Exemple simple : validation d'un code postal / courriel / longueur d'un champ trimmé

Voici un petit exemple Kotlin avec JUnit 4/5 (selon votre configuration Gradle). On montre une fonction de validation et plusieurs tests correspondants.

```kotlin
// src/main/kotlin/validation/Validators.kt
object Validators {
    fun isPostalCodeValid(code: String?): Boolean {
        if (code == null) return false
        val trimmed = code.trim()
        // exemple simple : 5 chiffres (adapter selon le pays)
        return trimmed.matches(Regex("^[0-9]{5}$"))
    }

    fun isEmailValid(email: String?): Boolean {
        if (email == null) return false
        val trimmed = email.trim()
        // regex simple pour l'exemple
        return trimmed.matches(Regex("^[^@\\s]+@[^@\\s]+\\.[^@\\s]+$"))
    }

    fun isFieldLengthOk(input: String?, min: Int): Boolean {
        if (input == null) return false
        val trimmed = input.trim()
        return trimmed.length >= min
    }
}
```

Tests correspondants (JUnit 5) :

```kotlin
// src/test/kotlin/validation/ValidatorsTest.kt
// imports volontairement omis dans l'exemple; utilisez @org.junit.jupiter.api.Test et les appels fully-qualified si nécessaire

class ValidatorsTest {

    @org.junit.jupiter.api.Test
    fun `postal code valid`() {
        org.junit.jupiter.api.Assertions.assertTrue(Validators.isPostalCodeValid("12345"))
    }

    @org.junit.jupiter.api.Test
    fun `postal code invalid`() {
        org.junit.jupiter.api.Assertions.assertFalse(Validators.isPostalCodeValid("12 345"))
        org.junit.jupiter.api.Assertions.assertFalse(Validators.isPostalCodeValid("abcde"))
        org.junit.jupiter.api.Assertions.assertFalse(Validators.isPostalCodeValid(null))
    }

    @org.junit.jupiter.api.Test
    fun `email valid and invalid`() {
        org.junit.jupiter.api.Assertions.assertTrue(Validators.isEmailValid("utilisateur@example.com"))
        org.junit.jupiter.api.Assertions.assertFalse(Validators.isEmailValid("utilisateur@"))
        org.junit.jupiter.api.Assertions.assertFalse(Validators.isEmailValid("   "))
    }

    @org.junit.jupiter.api.Test
    fun `field length trimmed`() {
        org.junit.jupiter.api.Assertions.assertTrue(Validators.isFieldLengthOk("  hello  ", 5))
        org.junit.jupiter.api.Assertions.assertFalse(Validators.isFieldLengthOk("  hi  ", 3))
    }
}
```

> Remarque : adaptez les noms de packages et la configuration Gradle/JVM selon votre projet.

## 5. Exécution des tests (IntelliJ / Gradle)

- IntelliJ : clic droit sur le dossier `src/test` → Run 'Tests in ...'.
- Gradle (terminal) :

```bash
./gradlew test
```

Sous Windows PowerShell :

```powershell
.\gradlew.bat test
```

Les rapports de tests sont générés dans `build/reports/tests/test/index.html`.

## 6. Tests Android (instrumentation)

- Les tests unitaires JVM (src/test) sont rapides et suffisent pour la logique métier.
- Les tests d'instrumentation (src/androidTest) s'exécutent sur device/emulateur et peuvent vérifier l'UI.
- Pour Espresso : écrire des tests qui interagissent avec les vues et vérifient l'état visible.

## 7. Intégrer les tests dans le workflow

- Exécuter la suite de tests avant une remise de TP.
- Ajouter une étape d'intégration continue (CI) pour exécuter les tests automatiquement.

## 8. Liens utiles

- JUnit 5 : https://junit.org/junit5/docs/current/user-guide/
- Kotlin testing guide : https://kotlinlang.org/docs/testing.html
- Gradle test configuration : https://docs.gradle.org/current/userguide/java_testing.html


---

Si tu veux, je peux :

- ajouter des exemples plus avancés (mocks avec Mockito / MockK),
- ajouter une page de recette montrant pas-à-pas l'ajout d'un test dans un projet existant,
- configurer un GitHub Actions de base pour exécuter les tests automatiquement.
