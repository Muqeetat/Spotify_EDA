# Overview

This project was created to test and apply my new knowledge in Python and its data analysis libraries, namely **Pandas**, **Matplotlib**, and **Seaborn**. By diving into my own **Spotify data**, I was able to analyze my listening habits and music preferences. This project serves as both a personal exploration of my music taste and a practical exercise in **data analysis**.

The data was sourced using Spotify's Web API via the **Spotipy** Python library to fetch my liked songs. I also requested my complete listening history from Spotify, which provided a foundation for my analysis. This dataset contains detailed information on the tracks I’ve listened to, including the artist names, track names, genres, and playtime.

# The Questions

Below are the key questions I aimed to answer in this project:

1. What are my top 10 favorite songs?
2. Who are my top 10 favorite artists?
3. What particular genres do I listen to most?
4. How frequently do I listen to music per month?
5. How diverse is my music taste?

# Tools I Used

To perform this analysis, I leveraged several powerful tools:

- **Python:** The backbone of my analysis, allowing me to process and analyze the data efficiently.
    - **Pandas:** For data manipulation and analysis.
    - **Matplotlib:** For visualizing trends and insights in my data.
    - **Seaborn:** To create advanced visualizations and further explore data relationships.
- **Spotipy:** A Python library that provides a simple interface to access the Spotify Web API and fetch user data.
- **Jupyter Notebooks:** A notebook interface that helped me combine code execution with narrative to explain each step of my analysis.
- **Visual Studio Code:** My go-to code editor for Python development and version control.
- **Git & GitHub:** Essential for version control and sharing my code, ensuring easy collaboration and project tracking.

# Data Preparation and Cleanup

This section outlines how I cleaned and prepared my data before analysis:

### Importing & Cleaning Data

The first step involved importing the necessary libraries and setting up the Spotipy API to fetch my Spotify data.

```python
import spotipy
import spotipy.util as util
from spotipy.oauth2 import SpotifyClientCredentials
import spotipy.oauth2 as oauth2

# API Authentication
CLIENT_ID = "your_client_id"
CLIENT_SECRET = "your_client_secret"
username = "your_spotify_username"
scope = "user-top-read user-library-read playlist-read-private playlist-read-collaborative user-read-recently-played"
redirect_uri = 'http://mysite.com/callback/'

# Fetch token and authenticate
token = util.prompt_for_user_token(username=username, scope=scope, client_id=CLIENT_ID, client_secret=CLIENT_SECRET, redirect_uri=redirect_uri)
sp = spotipy.Spotify(auth=token)
```

I also performed the necessary data cleaning, which involved:
- Dropping rows with missing values.
- Converting timestamps into datetime objects for easy time-based analysis.
- Removing duplicate entries.

# The Analysis

### 1. What are my top 10 favorite songs?

To determine my favorite songs, I grouped the data by `track_name` and `artist_name`, and then counted the occurrences of each. This helped me identify the most frequently played tracks.

### Visualization:

```python
sns.barplot(data=df_ext_listen_count.head(10), x='song_count', y='track_name', palette='mako')
plt.title('Top 10 Most Listened-to Songs', fontsize=16, weight='bold')
plt.xlabel('Play Count')
plt.ylabel('Track Name')
plt.show()
```

### Results:

The analysis showed that my top 10 favorite songs are dominated by:
- **San Joseph** with the song *How to Miss You*.
- Frequent plays of artists like **Blake Rose**, **Lauv**, **Troye Sivan**, and **Harry Styles**.

### Insights:
- I listened to a lot of music in April 2024, with a total play count of 808 tracks.
  
### 2. How diverse is my music taste?

To measure the diversity of my music taste, I analyzed the genres I listen to. I extracted the `genres` data, split it into individual keywords, and then counted the occurrences.

### Visualization:

```python
sns.barplot(data=top_genres, x='count', y='genre_keyword')
plt.title('Top Genres', fontsize=16)
plt.xlabel('Count')
plt.ylabel('Genre')
plt.show()
```

### Insights:
- **Pop** is the dominant genre in my music library, with a strong inclination towards **indie pop** and **alternative pop**.
- This shows that my music taste is not very diverse, as it largely revolves around a few core genres.

# Challenges Faced

- **Data Inconsistencies:** Some inconsistencies in the listening data required careful handling, such as duplicate or missing entries.
- **API Integration:** Working with the Spotify API through Spotipy was a learning curve, particularly in handling authentication and making API calls.
- **Complex Data Visualization:** Designing effective visual representations of complex datasets was challenging but essential for conveying insights.

# Insights

Through this project, I gained a deeper understanding of:
- **Listening Trends:** I found that my listening habits are concentrated around a few core genres and artists.
- **Diversity in Music Taste:** My music taste, while diverse to some extent, is heavily skewed towards pop genres.
- **Monthly Listening Patterns:** There were spikes in listening activity during certain months.

# What I Learned

- **Advanced Python:** This project improved my skills in Python, particularly in using libraries like Pandas for data manipulation and Seaborn for advanced visualization.
- **Data Cleaning and Preprocessing:** I learned the importance of thorough data cleaning to ensure the accuracy and integrity of my analysis.
- **Working with APIs:** Using Spotify’s Web API via Spotipy provided valuable experience in working with APIs, including handling authentication and fetching user-specific data.

# Conclusion

This Spotify data analysis project was an exciting and informative experience. It allowed me to apply my newly acquired skills in data analysis and Python programming while gaining insights into my own music habits. The project has laid a solid foundation for future data analysis work and opened up avenues for exploring more advanced topics in data engineering.
