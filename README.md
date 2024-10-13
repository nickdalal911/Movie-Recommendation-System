# Movie Recommendation System

This web app recommends movies based on a selected movie using a collaborative filtering model. It fetches movie posters and provides suggestions using data from **The Movie Database (TMDb)** API.

You can explore the live app [here](https://movie-recommendation-system-lrb5ut8ktaq79w4fetqbdt.streamlit.app/).

## Features

- **Movie Suggestions:** Recommends five similar movies based on the user's selection.
- **Poster Display:** Shows the poster of each recommended movie.
- **Interactive UI:** Simple and intuitive interface built using Streamlit.

## How It Works

1. **Data:** The model is trained on movie data, using a similarity matrix stored in a `.pkl` file.
2. **TMDb API:** The app fetches movie posters using the TMDb API.
3. **Recommendation:** Based on the selected movie, the app calculates similarity scores to suggest movies most related to the one selected.

## Setup and Installation

To run this app locally, follow these steps:

1. Clone the repository or download the files.
   
2. Install the required libraries:
   ```bash
   pip install -r requirments.txt
   ```

3. Place the following files in the same directory as the main script:
   - `movie_dict.pkl`: Contains the movie data in dictionary format.
   - `similarity.pkl`: Contains the precomputed similarity matrix.

4. Run the Streamlit app:
   ```bash
   streamlit run app.py
   ```

## TMDb API Integration

To fetch movie posters, the app uses the TMDb API. Make sure to replace the API key in the code with your own from [TMDb](https://www.themoviedb.org/documentation/api).

```python
def fetch_poster(movie_id):
    response = requests.get('https://api.themoviedb.org/3/movie/{}?api_key=<YOUR_API_KEY>&language=en-US'.format(movie_id))
    data = response.json()
    poster_path = data.get('poster_path')
    return f"https://image.tmdb.org/t/p/w500/{poster_path}"
```

## Future Improvements

- Improve error handling for API requests.
- Add more advanced recommendation features such as genre-based filtering or hybrid models.
- Enhance the UI/UX for a better user experience.

