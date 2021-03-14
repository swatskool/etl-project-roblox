# etl-project-roblox

Project Proposal: We will create a service that will allow users to view the most popular Roblox game and display the top youtube tutorials on how to play the Roblox game. We will accomplish this by scraping information from the Roblox site for the most engaging game, query the Youtube API for the top 5 videos of the search for each game, and display each game with the top 5 tutorial videos on our service.

We scraped game information from the Roblox website as our starting point. Roblox has multiple categories of games to select from, with approximately 60 games for each category. We limited our scope to include games from the Most Engaging category to limit our project scope and include only the best games for gamers in our end service.

The Roblox site uses Javascript.  When viewing the site, more content is available than is available immediately using a simple scrape.  As a result, it was necessary to enable the Web Driver for the browser to allow faster loading speeds to facilitate scraping.

We pulled the game title, thumbnail of the game, url for the game, user rating, and number of players to capture the game and it's popularity.

We transformed the data to reflect the user rating as a number from 0 to 100 rather than a percentage to allow us to sort the games by user ratings. We also updated the game titles to ensure the game names return good results in our Youtube API.

Using a static key word search and the game names returned from the web scrape, we queried the video titles, durations, comment counts, like counts, and view counts for the top 5 results returned from Youtube on "learn to play <roblox_game>".

Once all our results were returned from both services, we created a PGAdmin SQL database to allow end users to query our results. We originally leaned towards a MongoDB dataframe since querying the dataframe is more user-friendly, but since our results were already in a tabular format (the preferred format of SQL dataframes) we elected to insert our results in a PGAdmin database.

Using the game_id as the primary key for the Roblox game table and tying that as the foreign key for the Youtube video table, we were able to successfully create a service that would return game results and the top Youtube tutorial results.