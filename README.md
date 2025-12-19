# Lab3-DeepLearning-Arabic

##  Partie 1 : Classification de Texte Arabe

### 1.1 Collecte de Données
- Utilisation de **BeautifulSoup** pour scraper des sites d'actualités arabes
- Collecte de textes sur le thème **"التعلم العميق"** (Deep Learning)
- Attribution manuelle/simulée de scores de pertinence (0-10)

### 1.2 Pipeline de Prétraitement
Implémentation d'un pipeline NLP complet pour l'arabe :
- **Nettoyage** : Suppression des caractères non-arabes
- **Normalisation** : Uniformisation des caractères arabes
- **Tokenization** : Découpage avec NLTK
- **Stopwords** : Suppression des mots vides arabes
- **Stemming/Lemmatization** : Réduction à la racine

### 1.3 Modèles Implémentés
Quatre architectures de séquences ont été implémentées :

| Modèle | Paramètres | Architecture |
|--------|------------|--------------|
| **RNN** | 59,905 | Simple Recurrent Neural Network |
| **LSTM** | 239,233 | Long Short-Term Memory |
| **GRU** | 179,457 | Gated Recurrent Unit |
| **BiRNN** | 152,577 | Bidirectional RNN |

### 1.4 Résultats de Classification

| Modèle | MSE | MAE | R² Score | Accuracy (±1) | BLEU |
|--------|-----|-----|----------|---------------|------|
| **RNN** | 2.3232 | 1.4628 | -0.4868 | 0.00% | 0.00 |
| **LSTM** | 7.5128 | 2.4133 | -3.8082 | 0.00% | 0.00 |
| **GRU** | 3.1890 | 1.3207 | -1.0410 | 50.00% | 0.00 |
| **BiRNN** | 2.1564 | 1.2875 | -0.3801 | 0.00% | 0.00 |

**Meilleur modèle :** Bidirectional RNN (MSE: 2.1564)

##  Partie 2 : Génération de Texte avec GPT-2

### 2.1 Fine-tuning GPT-2
- Chargement du modèle **GPT-2 pré-entraîné**
- Adaptation sur dataset arabe personnalisé
- Entraînement sur 2 époques avec learning rate adaptatif

### 2.2 Résultats de Génération

**Avant fine-tuning :**
Prompt: "التعلم العميق"
Généré: "بصرادة فاهد وسنوب م - Fahrenkab, 'Al A'qam (the Most High) of the Sunnah..."

**Après fine-tuning :**
Prompt: "التعلم العميق هو مجال مهم"
Généré: "التعلم العميق هو مجال مهم رسبة واعرد ان: Al-Majlis, al-Nawaharaya', p. 34..."

### 2.3 Observations
- ✅ Réduction de la loss (2.33 → 1.82)
- ✅ Augmentation de la proportion d'arabe généré
- ❌ **Problème** : Mélange arabe/anglais persistant
- ❌ **Limitation** : Dataset insuffisant (50 textes seulement)

### 2.4 Solutions Proposées
1. **AraGPT2** : Modèle spécifiquement pré-entraîné sur arabe
2. **Dataset plus grand** : 500+ textes arabes purs
3. **Filtrage par langue** : Post-processing pour garantir l'arabe

##  Synthèse des Apprentissages

###  Ce qui a fonctionné
1. **Collecte de données** : BeautifulSoup efficace pour le scraping arabe
2. **Prétraitement** : Pipeline robuste pour la langue arabe
3. **Implémentation PyTorch** : Création et entraînement des modèles
4. **Fine-tuning GPT-2** : Adaptation basique fonctionnelle
5. **Évaluation** : Métriques multiples et pertinentes

###  Difficultés rencontrées
1. **Données limitées** : Difficulté à collecter suffisamment de textes arabes
2. **Mélange linguistique** : GPT-2 tend à revenir à l'anglais
3. **Performance modèles** : Scores de classification à améliorer
4. **Ressources computationnelles** : Fine-tuning gourmand en GPU

###  Apprentissages Clés
1. **L'importance des données** : Qualité et quantité cruciales pour le NLP
2. **Spécificités de l'arabe** : Nécessité d'un prétraitement adapté
3. **Limitations des modèles généraux** : GPT-2 non optimisé pour l'arabe
4. **Évaluation holistique** : Au-delà des métriques, analyse qualitative essentielle
5. **Optimisation pratique** : Batch sizing, learning rate scheduling, early stopping

###  Perspectives d'Amélioration
1. **Modèles arabes spécialisés** : AraBERT, AraGPT2, CAMeL
2. **Augmentation de données** : Traduction, paraphrasing, scraping intensif
3. **Techniques avancées** : Transfer learning, few-shot learning, prompt engineering
4. **Évaluation renforcée** : Métrics spécifiques arabe, évaluation humaine



****Ce laboratoire m'a permis de maîtriser plusieurs compétences essentielles en Deep Learning pour le NLP :

Maîtrise de PyTorch : Implémentation de modèles complexes

Traitement de l'arabe : Adaptation des techniques NLP aux spécificités de la langue

Architectures de séquences : Compréhension approfondie de RNN, LSTM, GRU

Fine-tuning de transformers : Adaptation de GPT-2 pour une tâche spécifique

Évaluation critique : Analyse des résultats et identification des limitations
