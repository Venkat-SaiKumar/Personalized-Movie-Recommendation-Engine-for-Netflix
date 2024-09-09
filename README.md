# Personalized-Movie-Recommendation-Engine-for-Netflix
Developed a personalized Movie Recommendation System using Python and Scikit-learn. Loaded and explored data from a CSV dataset, created a 'tags' feature by combining attributes, used CountVectorizer for text vectorization, and calculated cosine similarity for movie suggestions. Future plans include collaborative filtering and more metadata.

This Python code builds a movie recommendation system using a dataset from TMDB (The Movie Database). The dataset includes movie metadata such as titles, genres, cast, crew, and keywords.

### Steps:
1. **Data Loading**: The code begins by loading two CSV files: `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv`.
2. **Data Merging**: The two datasets are merged based on the movie title to combine important features like movie genres, keywords, cast, and crew.
3. **Data Cleaning & Transformation**: 
   - The `genres`, `keywords`, `cast`, and `crew` columns are transformed from JSON-like strings into lists of relevant names (e.g., genres like "Action," cast members like "Johnny Depp").
   - For simplicity, only the top 3 cast members are retained, and only the director from the crew is kept.
   - The features are cleaned by collapsing multi-word names into single strings without spaces.
4. **Feature Engineering**: 
   - The `tags` column is created by combining the `overview`, `genres`, `keywords`, `cast`, and `crew` columns into a single list of words.
5. **Vectorization**: The `tags` column is vectorized using the `CountVectorizer`, which converts the text into a matrix of token counts, with a maximum of 5,000 features, while ignoring English stop words.
6. **Cosine Similarity**: A cosine similarity matrix is computed to measure the similarity between different movies based on the `tags`.
7. **Recommendation System**: 
   - A `recommend()` function is created. Given a movie title, the function calculates the most similar movies using the cosine similarity matrix and returns the top 5 recommendations.
   - For example, if the movie "Gandhi" is input, the system recommends related films like "Gandhi, My Father" and "A Passage to India."
8. **Model Saving**: The data (with the new `tags` column) and the similarity matrix are serialized and saved using `pickle`, allowing the model to be reused without recalculating the matrix.

This recommendation system provides content-based movie suggestions by analyzing the textual metadata of films, focusing on genres, keywords, cast, and crew.
