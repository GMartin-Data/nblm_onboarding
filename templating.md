# Step 1: Deep Research
## Prompt Template
```markdown
"Recherche et importe des sources pédagogiques sur l'écosystème '{{DOMAINE_TECHNIQUE}}'.
Focus : Expliquer {{LISTE_OUTILS}} à des {{PERSONA_CIBLE}}. Priorise les concepts de {{CONCEPTS_CLES}}. Contrainte : Exclus {{CONTENUS_A_EXCLURE}} et privilégie les guides orientés '{{NIVEAU_EXPERTISE}}'."
```

# Step 2: Filtrage
## Prompt Template
```markdown
Agis en tant que {{ROLE_EXPERT}}. Analyse les {{NOMBRE_SOURCES}} sources pour construire un parcours d'onboarding {{SUJET}} destiné à des profils {{PERSONA_CIBLE}}.

Identifie et sélectionne uniquement les {{NOMBRE_SOURCES_FINALES}} sources les plus pertinentes selon cette structure :
1. {{PILIER_1}} ({{N}} sources) : {{DESCRIPTION_PILIER_1}}.
2. {{PILIER_2}} ({{N}} sources) : {{DESCRIPTION_PILIER_2}}.
3. {{PILIER_3}} ({{N}} sources) : {{DESCRIPTION_PILIER_3}}.
4. {{PILIER_4}} ({{N}} sources) : {{DESCRIPTION_PILIER_4}}.

Pour chaque source retenue, indique :
- Le concept clé à retenir pour un {{PERSONA_CIBLE}}.
- Pourquoi elle remplace d'autres sources similaires (Élimination de la redondance).
- Une consigne claire : "GARDER EN PRIORITÉ".

Pour TOUTES les autres sources (y compris paywalls et docs trop techniques), liste-les sous une section "À SUPPRIMER" avec une justification courte.
```

# Step 3: Organisation
## Prompt
```markdown
Agis comme un bibliothécaire technique. Pour chacune des {{NOMBRE_SOURCES}} sources présentes dans ce notebook ({{LISTE_PREFIXES}}), propose-moi un titre court et explicite de 3 à 5 mots maximum qui résume le contenu spécifique. Exemple de format attendu : > - '{{PREFIXE_EXEMPLE}} - ...' devient : '{{PREFIXE_EXEMPLE}} - {{TITRE_EXEMPLE}}'
```

# Step 4: Golden Source
## Prompt Template
```markdown
# MISSION
Synthétiser les {{NOMBRE_SOURCES}} sources actuelles pour créer un manuel d'onboarding unique, cohérent et technique, destiné à des profils {{PERSONA_CIBLE}}.

# OBJECTIF DE LA SOURCE
Ce document doit devenir la "Source de Vérité" (Golden Source) du Notebook. Il doit éliminer les redondances et harmoniser les concepts entre {{LISTE_OUTILS}}.

# STRUCTURE ATTENDUE (À rédiger de manière exhaustive)
1. INTRODUCTION : {{DESCRIPTION_INTRO}}.
2. {{SECTION_1}} : {{DESCRIPTION_SECTION_1}}.
3. {{SECTION_2}} : {{DESCRIPTION_SECTION_2}}.
4. {{SECTION_3}} : {{DESCRIPTION_SECTION_3}}.
5. {{SECTION_4}} : {{DESCRIPTION_SECTION_4}}.
6. LEXIQUE {{DOMAINE}}-TECHNIQUE : Table de correspondance des termes.

# RÈGLES DE RÉDACTION (CRUCIAL POUR L'IMPORTATION)
- Ne fais pas de commentaires type "Voici une synthèse". Rédige directement le contenu du manuel.
- Utilise un format Markdown structuré (Titres # et ##).
- Cite les sources d'origine entre crochets [Ex: {{PREFIXE_EXEMPLE}}] à la fin de chaque paragraphe clé pour maintenir le lignage.
- Assure-toi que le texte est "Self-contained" (il doit se suffire à lui-même).
```

# Step 5: Customisation du System Prompt du Chat
## Prompt Template
```markdown
# PERSONA
Tu es l'Expert {{DOMAINE}} de l'entreprise. Ton rôle est d'accompagner des profils {{PERSONA_CIBLE}} dans l'apprentissage de {{SUJET}}. Tu es pédagogue, précis, et tu mets toujours en avant {{VALEURS_CLES}}.

# HIÉRARCHIE DES SOURCES (CRUCIAL)
1. PRIORITÉ ABSOLUE : Utilise toujours la source "{{NOM_GOLDEN_SOURCE}}" pour structurer tes réponses.
2. DÉTAILS TECHNIQUES : Utilise les sources "{{LISTE_SOURCES_SECONDAIRES}}" uniquement pour approfondir un point spécifique ou répondre à une demande de précision technique.
3. SI UNE INFORMATION MANQUE : Si la réponse n'est dans aucune source, admets-le honnêtement et suggère de consulter {{EQUIPE_REFERENCE}}. Ne simule jamais de connaissances hors contexte.

# STYLE DE RÉPONSE
- CLARTÉ : Pas de jargon technique sans explication. Traduis les termes (ex: {{EXEMPLE_TRADUCTION}}).
- CITATIONS : Identifie systématiquement la source de tes informations avec des balises type [{{PREFIXE_SOURCE}}].
- STRUCTURE : Utilise des listes à puces et des paragraphes courts.
- ENGAGEMENT : Termine chaque réponse par une question de validation ou une suggestion de mise en pratique pour l'apprenant.

# INTERDICTIONS
- Ne jamais suggérer {{CONTENUS_INTERDITS}} aux profils {{PERSONA_CIBLE}}.
- Ne pas dériver sur des sujets hors de {{PERIMETRE_SUJET}}.
```

# Step 6: Output de la Golden Source (Slide Deck)
## Prompt Template
```markdown
# ROLE
Agis en tant que {{ROLE_SENIOR}}. Ton objectif est de transformer la documentation technique en une présentation de haut niveau pour {{AUDIENCE_CIBLE}}.

# DOCUMENT DE RÉFÉRENCE
Utilise exclusivement la source : {{NOM_GOLDEN_SOURCE}}.

# FORMAT & TON
- Format : Detailed Deck ({{NOMBRE_SLIDES}} slides).
- Ton : {{TON_SOUHAITE}}.
- Style Visuel : {{STYLE_VISUEL}}.

# STRUCTURE NARRATIVE DES SLIDES
1. TITRE : "{{TITRE_PRESENTATION}}".
2. VISION : {{DESCRIPTION_VISION}}.
3. {{OUTIL_1}} : {{METAPHORE_1}}. {{DESCRIPTION_SLIDE_1}}.
4. {{OUTIL_2}} : {{METAPHORE_2}}. {{DESCRIPTION_SLIDE_2}}.
5. {{OUTIL_3}} : {{METAPHORE_3}}. {{DESCRIPTION_SLIDE_3}}.
6. GOUVERNANCE : {{DESCRIPTION_GOUVERNANCE}}.
7. CONCLUSION : {{DESCRIPTION_CONCLUSION}}.

# INSTRUCTIONS SPÉCIFIQUES
- Utilise des métaphores business pour chaque outil.
- Inclus une slide dédiée au concept de "Single Source of Truth" (Source de Vérité Unique).
- Chaque slide doit comporter un "Key Takeaway" (Point clé à retenir) pour un décideur {{PERSONA_CIBLE}}.
- Ne pas inclure {{ELEMENTS_A_EXCLURE}}.
```

---
---

# Module X: Filtrage des Sources
## Prompt Template
```markdown
# ROLE
Agis en tant que Context Manager & {{ROLE_EXPERT}}. Ton objectif est d'optimiser la fenêtre de contexte (RAG) pour la rédaction d'un module spécifique.

# TÂCHE
Analyse l'intégralité des sources actuellement présentes dans ce notebook (titres et résumés de contenu).
Je m'apprête à travailler sur le **{{NOM_MODULE}} : {{TITRE_MODULE}}**.

# OBJECTIF DU MODULE
{{LISTE_OBJECTIFS_MODULE}}

# SORTIE ATTENDUE
Dresse deux listes distinctes :
1. **SOURCES À GARDER COCHÉES** : {{CRITERES_SOURCES_A_GARDER}}.
2. **SOURCES À DÉCOCHER** : {{CRITERES_SOURCES_A_EXCLURE}}.

# JUSTIFICATION
Pour chaque source à décocher, explique brièvement pourquoi elle risque de créer du "bruit" ou des confusions sémantiques pour le sujet {{SUJET_MODULE}}.
```

# Module X: Création du Cours via le Chat
## Prompt Template
```markdown
# MISSION
Agis en tant que {{ROLE_EXPERT}}. Analyse les sources sélectionnées pour rédiger le contenu exhaustif du "{{NOM_MODULE}} : {{TITRE_MODULE}}".

# STRUCTURE DU COURS
1. {{SECTION_1_TITRE}} ({{ANGLE_1}}) :
   - {{POINT_1_1}}
   - {{POINT_1_2}}

2. {{SECTION_2_TITRE}} ({{ANGLE_2}}) :
   - {{POINT_2_1}}
   - {{POINT_2_2}}

3. {{SECTION_3_TITRE}} ({{ANGLE_3}}) :
   - {{POINT_3_1}}
   - {{POINT_3_2}}

4. {{SECTION_4_TITRE}} ({{ANGLE_4}}) :
   - {{POINT_4_1}}
   - {{POINT_4_2}}

# EXIGENCES TECHNIQUES
- GROUNDING : Cite systématiquement tes sources pour chaque affirmation technique.
- TON : {{TON_SOUHAITE}}.
- VALEUR AJOUTÉE : {{LIEN_AVEC_AUTRES_MODULES}}.
- QUIZ : Propose {{NOMBRE_QUESTIONS}} questions de validation "{{NIVEAU_QUIZ}}" ({{DESCRIPTION_NIVEAU_QUIZ}}).
```

# Module X: Infographie
## Prompt Template
```markdown
# MISSION
Créer une infographie pédagogique intitulée : "{{TITRE_INFOGRAPHIE}}".

# STRUCTURE VISUELLE
1. {{SECTION_VISUELLE_1}} : {{DESCRIPTION_1}}.
2. {{SECTION_VISUELLE_2}} : {{DESCRIPTION_2}}.
3. {{SECTION_VISUELLE_3}} : {{DESCRIPTION_3}}.
4. {{SECTION_VISUELLE_4}} : {{DESCRIPTION_4}}.

# STYLE
{{DESCRIPTION_STYLE}}.
Message clé : "{{MESSAGE_CLE}}".
```

# Module X: Data Table
## Prompt Template
```markdown
# MISSION
Génère une "Data Table" comparative pour aider les utilisateurs {{PERSONA_CIBLE}} à {{OBJECTIF_TABLE}}.

# OBJECTIF MÉTIER
{{DESCRIPTION_OBJECTIF_METIER}}.

# STRUCTURE DU TABLEAU (Colonnes requises)
1. {{COLONNE_1}} (ex: {{EXEMPLE_1}}).
2. {{COLONNE_2}} ({{OPTIONS_COLONNE_2}}).
3. {{COLONNE_3}} ({{DESCRIPTION_COLONNE_3}}).
4. {{COLONNE_4}} ({{DESCRIPTION_COLONNE_4}}).

# LIGNES À ANALYSER (Basé sur les sources)
{{LISTE_LIGNES}}

# CONTRAINTES DE RÉDACTION
- {{CONTRAINTE_1}}.
- {{CONTRAINTE_2}}.
- Ton : {{TON_SOUHAITE}}.
```

# Slide Deck de Synthèse Multi-Modules
## Prompt Template
```markdown
# MISSION
Générer un Slide Deck de synthèse détaillé intitulé : "{{TITRE_SLIDE_DECK}}".

# STRUCTURE DES SLIDES ({{NOMBRE_SLIDES}} Slides)
1. TITRE : {{TITRE_SLIDE_1}}.
2. {{THEME_SLIDE_2}} : {{DESCRIPTION_SLIDE_2}}.
3. {{THEME_SLIDE_3}} : {{DESCRIPTION_SLIDE_3}}.
4. {{THEME_SLIDE_4}} : {{DESCRIPTION_SLIDE_4}}.
5. {{THEME_SLIDE_5}} : {{DESCRIPTION_SLIDE_5}}.
6. {{THEME_SLIDE_6}} : {{DESCRIPTION_SLIDE_6}}.
7. CONCLUSION : {{DESCRIPTION_CONCLUSION}}.

# EXIGENCES
- Utiliser un ton "{{TON_SOUHAITE}}".
- S'appuyer exclusivement sur les faits techniques des sources ({{TYPES_FAITS_A_INCLURE}}).
```
