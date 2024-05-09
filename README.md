# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Start coding!
#read csv files
netflix_df=pd.read_csv("netflix_data.csv")

#removed TV shows
netflix_subset=netflix_df[netflix_df["type"]!="TV Show"]

#keep 5 column
netflix_movies=netflix_subset.loc[:,["title", "country", "genre", "release_year", "duration"]]

#Movies that are shorter than 60 minutes
short_movies=netflix_movies[netflix_movies["duration"]<60]

colors=[]
for lab,row in netflix_movies.iterrows():
    if row["genre"]=="Children":
        colors.append('red')
    elif row["genre"]=="Documentaries":
        colors.append('blue')
    elif row["genre"]=="Stand-Up":
        colors.append('green')
    else:
       colors.append('black')

    colors[:10]
    
# set figure
fig=plt.figure(figsize=(12,8))

#Create scatter plot
plt.scatter(netflix_movies.release_year,netflix_movies.duration,c=colors)

#Create title and labels
plt.xlabel("Release year")
plt.ylabel("Duration (min)")
plt.title("Movie Duration by Year of Release")

plt.show()

answer="no"
