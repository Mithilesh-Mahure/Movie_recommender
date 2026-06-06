# 🎬 Movie Recommender System

A content-based movie recommendation engine that suggests similar movies based on genres, keywords, cast, crew, and plot overview using natural language processing and cosine similarity.

## 📋 Overview

This project implements a **content-based filtering** approach to recommend movies. Given a movie title, the system analyzes various features (genres, keywords, cast, crew, and synopsis) and returns the 5 most similar movies using **TF-IDF vectorization** and **cosine similarity**.

The recommendation model is built on the TMDB (The Movie Database) dataset containing 4,809 movies with comprehensive metadata.

## 🚀 Quick Start

### Test the Recommender

```python
recommend('Avatar')
# Output:
# Titan A.E.
# Independence Day
# Ender's Game
# Aliens vs Predator: Requiem
# Battle: Los Angeles
```

Or try:
```python
recommend('Batman Begins')
# Output:
# The Dark Knight
# The Dark Knight Rises
# Batman
# Batman & Robin
# Batman
```

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.11-3776ab?style=flat-square&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37726?style=flat-square&logo=jupyter)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=flat-square&logo=pandas)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?style=flat-square&logo=scikit-learn)
![NLTK](https://img.shields.io/badge/NLTK-NLP-green?style=flat-square)

## 📚 Libraries Used

- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computations
- **Scikit-learn** - Machine learning algorithms (CountVectorizer, cosine_similarity)
- **NLTK** - Natural Language Processing (Porter Stemmer for text normalization)

## 🔧 How It Works

### 1. **Data Preparation**
   - Loads TMDB movies and credits datasets
   - Merges datasets on movie title
   - Selects relevant features: genres, keywords, cast, crew, overview

### 2. **Feature Engineering**
   - Extracts genre names from JSON-like structures
   - Extracts top 3 cast members for each movie
   - Extracts director information from crew data
   - Tokenizes movie overviews into words

### 3. **Text Processing**
   - Removes spaces from text features
   - Converts all text to lowercase
   - Applies Porter Stemming for word normalization
   - Combines all features into a single "tags" column

### 4. **Vectorization**
   - Uses **CountVectorizer** with max 5000 features
   - Removes English stop words
   - Converts text tags to TF (Term Frequency) vectors

### 5. **Similarity Computation**
   - Calculates **Cosine Similarity** between all movie vectors
   - For a given movie, finds the 5 movies with highest similarity scores
   - Returns recommendations excluding the input movie itself

## 📊 Dataset

**Source:** [TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata?select=tmdb_5000_credits.csv)

**Files Required:**
- `tmdb_5000_movies.csv` - Movie metadata (4,809 movies)
- `tmdb_5000_credits.csv` - Cast and crew information

**Key Columns Used:**
- `title` - Movie name
- `genres` - JSON array of genres
- `keywords` - JSON array of relevant keywords
- `cast` - JSON array of actors
- `crew` - JSON array of crew members
- `overview` - Movie synopsis

## 📝 Recommendation Algorithm

```
1. Input: Movie Title
2. Find movie index in dataset
3. Retrieve similarity scores for that movie against all others
4. Sort by similarity score (descending)
5. Return top 5 movies (excluding the input movie)
6. Output: List of 5 recommended movie titles
```

## 🎯 Key Features

✅ **Content-Based Filtering** - Recommends based on movie characteristics, not user ratings  
✅ **Multi-Feature Analysis** - Considers genres, keywords, cast, director, and plot  
✅ **Text Normalization** - Porter Stemming for robust text matching  
✅ **Scalable** - Works efficiently with 4,800+ movies  
✅ **No Cold Start Problem** - Works for new movies without user history  

## 📈 Performance Considerations

- **Vectorization**: 5,000 features max for computational efficiency
- **Stop Words**: English stop words removed to focus on meaningful terms
- **Stemming**: Reduces vocabulary size and improves matching accuracy

## 🤝 Future Enhancements

- Add user-based collaborative filtering
- Implement hybrid recommendation approach
- Add rating/vote average as weighting factor
- Create a web interface for interactive recommendations
- Add popularity metrics to rankings
- Include budget and revenue features

## 📄 License

This project is open source and available for educational purposes.

## 📞 Contact & Contributing

Feel free to fork, modify, and improve this project!

---

**Created with ❤️ for movie enthusiasts**
