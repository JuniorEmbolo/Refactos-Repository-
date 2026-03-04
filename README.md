# CI/CD avec GitHub Actions

## Workflow actuel
- Nom : Java CI avec Maven
- Fichier : `.github/workflows/ci-maven.yml` (ou le nom que tu as utilisé)
- Déclencheurs :
  - push sur main
  - pull_request vers main
  - lancement manuel (workflow_dispatch)
- Ce qu'il fait :
  1. Récupère le code (checkout)
  2. Installe Java 21 (Temurin)
  3. Cache Maven (accélère beaucoup)
  4. `mvn package` → compile + crée le JAR
  5. `mvn test` → lance les tests (si présents)
  6. Upload le JAR comme artifact (téléchargeable après run)

## Comment contribuer / tester des changements au CI
1. Crée une branche depuis main :
   git checkout -b nom-prenom-amelioration-ci
2. Modifie `.github/workflows/ci-maven.yml` (ou ajoute un nouveau si expérimental)
3. Commit & push :
   git push origin nom-prenom-amelioration-ci
4. Ouvre une Pull Request vers main
5. Le CI existant tourne automatiquement sur ta PR → tu vois si ton changement casse quelque chose
6. Demande review → merge quand OK

## Règles
- Toujours tester localement avant (mvn clean package)
- Garder le workflow simple et lisible
- Pas de duplication : on améliore le workflow partagé
