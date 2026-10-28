# Copilot Context — Simulateur de cache & coût (Material 3)

Outil HTML autonome et sans dépendance externe permettant d'estimer l'impact du prompt cache sur **le coût d'entrée d'un appel GitHub Copilot**.

## Trois réglages essentiels

1. **Modèle** : sélection OpenAI, Anthropic et Google.
2. **Limite de la context window** : 128K, 200K, 272K, 1M ou 1,128M tokens.
3. **Tokens du contexte actuel** : curseur réglable jusqu'à la capacité disponible (buffer approximatif de 15 % déjà réservé).

Les deux coûts (**Avec cache** et **Sans cache**) sont présentés en permanence côte à côte, mettant directement en valeur l'impact du prompt cache et les économies potentielles. Le style adopte les surfaces tonales, formes arrondies et curseurs inspirés de **Material Design 3**.

Le réglage « tokens du contexte actuel » est une **approximation du volume d'entrée actif réutilisable depuis le cache**, à distinguer du compteur cumulé de tokens d'une session.

## Limites du calcul

- Calcul : `tokens × (prix par million de tokens) / 1 000 000 × 100 = AI credits`.
- Comparaison de **deux extrêmes** : 100 % des tokens d'entrée réutilisés au tarif cached input, contre 100 % au tarif normal. En réalité, une requête peut combiner les deux.
- Le tarif **Long context** s'applique si le nombre de tokens d'entrée dépasse le seuil tarifaire du modèle ; la simple sélection d'une capacité d'1M ne suffit pas.
- Les coûts de **sortie**, de **cache write** et des **nouveaux tokens** ne sont pas inclus pour conserver des réglages simples. Le résultat n'est donc **pas le coût complet d'un appel**.
- Le buffer est une **réserve de capacité**, pas des tokens facturés. L'outil utilise un buffer approximatif de 15 % ; Copilot peut en utiliser un autre.
- La disponibilité des grandes fenêtres de contexte dépend du modèle et de l'interface Copilot ; la sélection d'une capacité dans l'outil ne la garantit pas.
- Le total d'AI credits calculé représente une consommation théorique, pas nécessairement un paiement supplémentaire, selon le plan et les crédits disponibles.

## Publication publique via GitHub Pages

1. Créer un dépôt GitHub public et y placer `index.html` à la racine.
2. Dans **Settings → Pages → Build and deployment**, sélectionner la branche `main` et le dossier `/ (root)`.
3. Partager l'URL produite par GitHub Pages. L'action **Partager** de l'interface peut inclure les réglages du simulateur dans un lien.

Le fichier `index.html` fonctionne aussi directement dans un navigateur sans connexion ni collecte de données.

## Sources

Tarifs en date du **26 octobre 2026** :
- https://docs.github.com/en/copilot/reference/copilot-billing/models-and-pricing
- https://docs.github.com/en/copilot/tutorials/optimize-ai-usage

Outil indépendant de GitHub, OpenAI, Anthropic et Google.
