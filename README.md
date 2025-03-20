# SEC DATABASE
# Team Name: 
G2

# Team Members
1. Alicia Jarvis - https://github.com/aliciajarvis-ai
2. Oliver Schouest - https://github.com/oschouest
3. Tejas Panicker - https://github.com/Tejas5012
4. Nitya Kottapally - https://github.com/nityakottapally1
5. Aman Sathani - https://github.com/amansathani

# Project Scenario
Alex Carter, a journalist covering NCAA Division I Football, is preparing a comprehensive wrap-up of the 2024 SEC season. With the season concluded, she wants to analyze the NFL draft picks from SEC teams, standout player performances, team trends, coaching changes, and other key developments within the conference. To ensure her article provides a unique and insightful perspective, she reaches out to a coworker for detailed SEC-specific data, including draft selections, player stats, team performance metrics, the SEC championship game and notable off-season moves. By leveraging this information, Alex aims to craft an in-depth analysis that sets her apart in the competitive world of sports journalism.

# Data Model

<img width="700" alt="image" src= "https://github.com/user-attachments/assets/cb287cc5-0321-4dd1-9bd8-74bcd3a3dc7c" />

# Data Dictionary

### Coaches
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| coach_id           | INT                    | Primary Key  | Unique identifier for each coach             |      |
| first_name         | VARCHAR(50)            | Attribute    | Coach's first name                           | 50   |
| last_name          | VARCHAR(50)            | Attribute    | Coach's last name                            | 50   |
| team_id            | INT                    | Foreign Key  | Links to Teams(team_id)                      |      |
| position           | ENUM('Head Coach', 'Offensive Coordinator', 'Defensive Coordinator', 'Special Teams') | Attribute    | Coach's role (e.g., Head Coach)             |      |
| years_experience   | INT                    | Attribute    | Years of coaching experience                 |      |

### Conferences
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| conference_id      | INT                    | Primary Key  | Unique identifier for each conference        |      |
| conference_name    | VARCHAR(100)           | Attribute    | Full name of the conference (e.g., SEC)      | 100  |
| abbreviation       | VARCHAR(10)            | Attribute    | Short code for the conference (e.g., SEC)    | 10   |

### Games
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| game_id            | INT                    | Primary Key  | Unique identifier for each game             |      |
| game_date          | DATE                   | Attribute    | Date the game was played                     |      |
| venue_id           | INT                    | Foreign Key  | Links to Venues(venue_id)                    |      |
| home_team_score    | INT                    | Attribute    | Score of the home team                       |      |
| away_team_score    | INT                    | Attribute    | Score of the away team                       |      |

### Injuries
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| injury_id          | INT                    | Primary Key  | Unique identifier for each injury           |      |
| player_id          | INT                    | Foreign Key  | Links to Players(player_id)                  |      |
| game_id            | INT                    | Foreign Key  | Links to Games(game_id)                      |      |
| injury_desc        | VARCHAR(255)           | Attribute    | Description of the injury                    | 255  |
| injury_status      | ENUM('Probable', 'Questionable', 'Out', 'Season-Ending') | Attribute    | Status of the injury (e.g., Out)        |      |

### Penalties
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| penalty_id         | INT                    | Primary Key  | Unique identifier for each penalty          |      |
| game_id            | INT                    | Foreign Key  | Links to Games(game_id)                      |      |
| player_id          | INT                    | Foreign Key  | Links to Players(player_id)                  |      |
| team_id            | INT                    | Foreign Key  | Links to Teams(team_id)                      |      |
| penalty_type       | VARCHAR(255)           | Attribute    | Type of penalty (e.g., Holding)              | 255  |
| yards_lost         | INT                    | Attribute    | Yards lost due to the penalty                |      |

### Player_Stats
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| stat_id            | INT                    | Primary Key  | Unique identifier for each stat entry       |      |
| game_id            | INT                    | Foreign Key  | Links to Games(game_id)                      |      |
| player_id          | INT                    | Foreign Key  | Links to Players(player_id)                  |      |
| passing_yards      | INT                    | Attribute    | Passing yards in the game                    |      |
| rushing_yards      | INT                    | Attribute    | Rushing yards in the game                    |      |
| receiving_yards    | INT                    | Attribute    | Receiving yards in the game                  |      |
| touchdowns         | INT                    | Attribute    | Total touchdowns scored                      |      |
| tackles            | INT                    | Attribute    | Total tackles made                           |      |
| sacks              | INT                    | Attribute    | Total sacks made                             |      |
| interceptions      | INT                    | Attribute    | Total interceptions made                     |      |

### Players
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| player_id          | INT                    | Primary Key  | Unique identifier for each player           |      |
| first_name         | VARCHAR(50)            | Attribute    | Player's first name                          | 50   |
| last_name          | VARCHAR(50)            | Attribute    | Player's last name                           | 50   |
| team_id            | INT                    | Foreign Key  | Links to Teams(team_id)                      |      |
| position           | ENUM('QB', 'RB', 'WR', 'TE', 'OL', 'DL', 'LB', 'DB', 'K', 'P') | Attribute    | Player's position (e.g., QB)               |      |
| jersey_number      | INT                    | Attribute    | Player's jersey number                       |      |
| class_year         | ENUM('Freshman', 'Sophomore', 'Junior', 'Senior', 'Graduate') | Attribute    | Player's academic year (e.g., Junior)       |      |

### Recruiting
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| recruit_id         | INT                    | Primary Key  | Unique identifier for each recruit          |      |
| first_name         | VARCHAR(50)            | Attribute    | Recruit's first name                         | 50   |
| last_name          | VARCHAR(50)            | Attribute    | Recruit's last name                          | 50   |
| committed_team_id  | INT                    | Foreign Key  | Links to Teams(team_id)                      |      |
| position           | ENUM('QB', 'RB', 'WR', 'TE', 'OL', 'DL', 'LB', 'DB', 'K', 'P') | Attribute    | Recruit's position (e.g., QB)               |      |
| star_rating        | INT                    | Attribute    | Recruit's star rating (1-5)                  |      |

### Team_Stats
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| stat_id            | INT                    | Primary Key  | Unique identifier for each stat entry       |      |
| game_id            | INT                    | Foreign Key  | Links to Games(game_id)                      |      |
| team_id            | INT                    | Foreign Key  | Links to Teams(team_id)                      |      |
| total_yards        | INT                    | Attribute    | Total offensive yards                        |      |
| passing_yards      | INT                    | Attribute    | Total passing yards                          |      |
| rushing_yards      | INT                    | Attribute    | Total rushing yards                          |      |
| turnovers          | INT                    | Attribute    | Total turnovers committed                    |      |
| penalties          | INT                    | Attribute    | Total number of penalties                    |      |
| penalty_yards      | INT                    | Attribute    | Total penalty yards                          |      |

### Teams
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| team_id            | INT                    | Primary Key  | Unique identifier for each team             |      |
| team_name          | VARCHAR(100)           | Attribute    | Full name of the team (e.g., Alabama)        | 100  |
| abbreviation       | VARCHAR(10)            | Attribute    | Short code for the team (e.g., ALA)          | 10   |
| conference_id      | INT                    | Foreign Key  | Links to Conferences(conference_id)          |      |

### Teams_has_Games
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| team_id            | INT                    | Primary Key, Foreign Key | Links to Teams(team_id)                |      |
| game_id            | INT                    | Primary Key, Foreign Key | Links to Games(game_id)                |      |
| role               | ENUM('Home', 'Away', 'Winner') | Attribute    | Role of the team in the game             |      |

### Venues
| Column Name        | Data Type/Format       | Role         | Description                                  | Size |
|--------------------|------------------------|--------------|----------------------------------------------|------|
| venue_id           | INT                    | Primary Key  | Unique identifier for each venue            |      |
| venue_name         | VARCHAR(255)           | Attribute    | Name of the stadium (e.g., Bryant


# Queries 
## First Query
The query asks for the top 5 passing performances within the quarterbacks of the SEC. This will help determine who the best and standouts quarterbacks are for her article so she can highlight them. 

```sql
SELECT p.first_name, p.last_name, t.team_name, ps.game_id, g.game_date, ps.passing_yards
FROM Player_Stats ps
JOIN Players p ON ps.player_id = p.player_id
JOIN Teams t ON p.team_id = t.team_id
JOIN Games g ON ps.game_id = g.game_id
WHERE ps.passing_yards > 0
ORDER BY ps.passing_yards DESC
LIMIT 5;
```
### Results
| first_name | last_name | team_name         | game_id | game_date  | passing_yards |
|------------|----------|------------------|---------|------------|--------------|
| Carson     | Beck     | Georgia Bulldogs | 1       | 2024-10-19 | 250          |
| Quinn      | Ewers    | Texas Longhorns  | 5       | 2024-12-07 | 200          |
| Quinn      | Ewers    | Texas Longhorns  | 1       | 2024-10-19 | 180          |
| Gunner     | Stockton | Georgia Bulldogs | 5       | 2024-12-07 | 71           |

---
## Second Query
This query shows the teams with the most penalties throughout the season. This will allow her to highlight which teams are “undisciplined” and perhaps young teams with little veteran leadership.  

```sql
SELECT t.team_name, SUM(ts.penalty_yards) AS total_penalty_yards, SUM(ts.penalties) AS total_penalties
FROM Team_Stats ts
JOIN Teams t ON ts.team_id = t.team_id
GROUP BY t.team_id, t.team_name
ORDER BY total_penalty_yards DESC;
```
### Results 
| team_name         | total_penalty_yards | total_penalties |
|------------------|--------------------|----------------|
| Georgia Bulldogs | 80                 | 10             |
| Texas Longhorns  | 75                 | 10             |
| Florida Gators   | 20                 | 3              |

---
## Third Query 
This query shows the players who were injured during the SEC Championship game. This is vital as this can impact, not only the game but the draft stock of players that are likely to declare for the NFL draft. All of which are important information for Alex to report on. 

```sql
SELECT p.first_name, p.last_name, t.team_name, i.injury_desc, i.injury_status
FROM Injuries i
JOIN Players p ON i.player_id = p.player_id
JOIN Teams t ON p.team_id = t.team_id
WHERE i.game_id = 5;
```
### Results 
| first_name | last_name | team_name         | injury_desc   | injury_status |
|------------|----------|------------------|--------------|--------------|
| Carson     | Beck     | Georgia Bulldogs | Elbow Injury | Out          |

---
## Fourth Query 
This query shows the top recruits based off of a star rating system. This is a list of the future talent that will go to the SEC schools. This is important for Alex as the dawgs have some major 5 star talent coming for the next season. 

```sql
SELECT t.team_name, r.first_name, r.last_name, r.position, r.star_rating
FROM Recruiting r
JOIN Teams t ON r.committed_team_id = t.team_id
WHERE r.star_rating = (
    SELECT MAX(star_rating)
    FROM Recruiting r2
    WHERE r2.committed_team_id = r.committed_team_id
)
ORDER BY r.star_rating DESC, t.team_name;
```
### Results 
| team_name         | first_name | last_name       | position | rating |
|------------------|------------|----------------|----------|--------|
| Georgia Bulldogs | Ellis      | Robinson IV    | DB       | 5      |
| Georgia Bulldogs | KJ         | Bolden         | DB       | 5      |
| Auburn Tigers    | Cam        | Coleman        | WR       | 4      |
| Texas Longhorns  | DJ         | Campbell       | OL       | 4      |
| Ole Miss Rebels  | Jadon      | Canady         | DB       | 3      |

---
## Fifth Query 
This query finds the player with the most tackles in the SEC Championship game to highlight the defensive star of the game. Alex will use this information to write a future piece about the top defensive players in the SEC over the last 10 years. 

```sql
SELECT p.first_name, p.last_name, t.team_name, ps.tackles
FROM Player_Stats ps
JOIN Players p ON ps.player_id = p.player_id
JOIN Teams t ON p.team_id = t.team_id
WHERE ps.game_id = 5 AND ps.tackles > 0
ORDER BY ps.tackles DESC
LIMIT 1;
```
### Results 
| first_name | last_name | team_name         | tackles |
|------------|-----------|------------------|--------|
| Malaki     | Starks    | Georgia Bulldogs | 8      |

---
## Sixth Query 
This query gets the overall team performance in the Championship game. This includes stuff like team passing and rushing yards, and also highlights team defensive performance.This is especially useful as Alex will be able to see which teams have been playing well overall in the game. These stats are insightful and will show which teams are performing. 

```sql
SELECT t1.team_name AS team, thg1.role, ts1.total_yards AS team_yards, ts1.passing_yards AS team_passing, 
	ts1.rushing_yards AS team_rushing, t2.team_name AS opponent, ts2.total_yards AS opponent_yards, 
	ts2.passing_yards AS opponent_passing, ts2.rushing_yards AS opponent_rushing
FROM Team_Stats ts1
JOIN Teams t1 ON ts1.team_id = t1.team_id
JOIN Teams_has_Games thg1 ON ts1.team_id = thg1.team_id AND ts1.game_id = thg1.game_id
JOIN Teams_has_Games thg2 ON ts1.game_id = thg2.game_id AND thg1.team_id != thg2.team_id
JOIN Team_Stats ts2 ON thg2.team_id = ts2.team_id AND thg2.game_id = ts2.game_id
JOIN Teams t2 ON ts2.team_id = t2.team_id
WHERE ts1.game_id = 5;
```
### Results 
| team    | role  | team_yards | team_passing | team_rushing | opponent  | opponent_yards | opponent_passing | opponent_rushing |
|------------------|---------|------------|--------------|--------------|------------------|----------------------|----------------------|----------------------|
| Texas Longhorns  | Away    | 340        | 200          | 140          | Georgia Bulldogs | 350                  | 71                   | 279                  |
| Georgia Bulldogs | Winner | 350        | 71           | 279          | Texas Longhorns  | 340                  | 200                  | 140                  |

---
## Seventh Query 
This query lists coaches in order of experience in order to better discuss coaching impact. This is huge as coaches like Nick Saban retired last season and typically the longer tenured a coach is, the better and more impactful they are. This will allow Alex to show which coaches have molded the teams to how they see fit with their impact. 

```sql
SELECT c.first_name, c.last_name, t.team_name, c.position, c.years_experience
FROM Coaches c
JOIN Teams t ON c.team_id = t.team_id
ORDER BY c.years_experience DESC;
```
### Results 
| first_name | last_name  | team_name                        | position                   | years_experience |
|------------|-----------|--------------------------------|------------------------|------------------|
| Brian      | Kelly     | LSU Tigers                     | Head Coach            | 25               |
| Kalen      | DeBoer    | Alabama Crimson Tide          | Head Coach            | 20               |
| Brent      | Venables  | Oklahoma Sooners              | Head Coach            | 20               |
| Kirby      | Smart     | Georgia Bulldogs              | Head Coach            | 18               |
| Mark       | Stoops    | Kentucky Wildcats             | Head Coach            | 16               |
| Sam        | Pittman   | Arkansas Razorbacks           | Head Coach            | 15               |
| Lane       | Kiffin    | Ole Miss Rebels               | Head Coach            | 15               |
| Steve      | Sarkisian | Texas Longhorns               | Head Coach            | 14               |
| Hugh       | Freeze    | Auburn Tigers                 | Head Coach            | 12               |
| Mike       | Elko      | Texas A&M Aggies              | Head Coach            | 12               |
| Shane      | Beamer    | South Carolina Gamecocks      | Head Coach            | 12               |
| Billy      | Napier    | Florida Gators                | Head Coach            | 10               |
| Todd       | Monken    | Georgia Bulldogs              | Defensive Coordinator | 10               |
| Eli        | Drinkwitz | Missouri Tigers               | Head Coach            | 10               |
| Josh       | Heupel    | Tennessee Volunteers          | Head Coach            | 10               |
| Clark      | Lea       | Vanderbilt Commodores         | Head Coach            | 8                |
| Kyle       | Flood     | Texas Longhorns               | Offensive Coordinator | 8                |
| Jeff       | Lebby     | Mississippi State Bulldogs    | Head Coach            | 8                |
| Dell       | McGee     | Georgia Bulldogs              | Offensive Coordinator | 5                |

---
## Eigth Query 
This query finds senior players who might be draft-eligible to predict NFL prospects. This is particularly useful for Alex as she will be able to write about the future draft prospects and will allow her to make her own mock draft for the NFL. 

```sql
SELECT p.first_name, p.last_name, t.team_name, p.position, p.class_year
FROM Players p
JOIN Teams t ON p.team_id = t.team_id
WHERE p.class_year = 'Senior'
ORDER BY t.team_name, p.last_name;
```
### Results 
| first_name | last_name | team_name                        | position | class_year  |
|------------|----------|---------------------------------|----------|--------|
| Carson     | Beck     | Georgia Bulldogs               | QB       | Senior |
| Raheim     | Sanders  | South Carolina Gamecocks      | RB       | Senior |
| Diego      | Pavia    | Vanderbilt Commodores         | QB       | Senior |

---
## Ninth Query 
This query lists all games with the winner and scores to summarize the season. This will allow Alex to analyze the trends of teams throughout the season and see the final rankings of the teams. 

```sql
SELECT g.game_id, g.game_date, v.venue_name,
       thg1_team.team_name AS home_team, g.home_team_score,
       thg2_team.team_name AS away_team, g.away_team_score,
       thg_winner_team.team_name AS winner
FROM Games g
JOIN Venues v ON g.venue_id = v.venue_id
JOIN Teams_has_Games thg1 ON g.game_id = thg1.game_id AND thg1.role IN ('Home', 'Winner')
JOIN Teams_has_Games thg2 ON g.game_id = thg2.game_id AND thg2.role = 'Away'
JOIN Teams_has_Games thg_winner ON g.game_id = thg_winner.game_id AND thg_winner.role = 'Winner'
JOIN Teams thg1_team ON thg1.team_id = thg1_team.team_id
JOIN Teams thg2_team ON thg2.team_id = thg2_team.team_id
JOIN Teams thg_winner_team ON thg_winner.team_id = thg_winner_team.team_id;
```
### Results 
| game_id | game_date  | venue_name         | home_team           | home_team_score | away_team           | away_team_score | winner             |
|---------|-----------|--------------------------------------------|---------------------|------------|---------------------|------------|---------------------|
| 4       | 2024-11-16 | Bryant-Denny Stadium                     | Alabama Crimson Tide | 27         | LSU Tigers          | 17         | Alabama Crimson Tide |
| 1       | 2024-10-19 | Sanford Stadium                          | Georgia Bulldogs    | 30         | Texas Longhorns     | 15         | Georgia Bulldogs    |
| 2       | 2024-11-02 | Sanford Stadium                          | Georgia Bulldogs    | 34         | Florida Gators      | 20         | Georgia Bulldogs    |
| 5       | 2024-12-07 | Mercedes-Benz Stadium                    | Georgia Bulldogs    | 22         | Texas Longhorns     | 19         | Georgia Bulldogs    |
| 3       | 2024-11-09 | Darrell K Royal-Texas Memorial Stadium  | Texas Longhorns     | 28         | Arkansas Razorbacks | 24         | Texas Longhorns     |

---
## Tenth Query 
This query finds games where penalties significantly impacted the outcome (high penalty yards for the losing team). This allows Alex to see the teams that are heavily penalized and see if there is a noticeable trend for teams that get penalized consistently. 

```sql
SELECT g.game_id, g.game_date, v.venue_name,
       thg_loser_team.team_name AS losing_team, ts.penalty_yards,
       thg_winner_team.team_name AS winning_team
FROM Games g
JOIN Venues v ON g.venue_id = v.venue_id
JOIN Teams_has_Games thg_winner ON g.game_id = thg_winner.game_id AND thg_winner.role = 'Winner'
JOIN Teams_has_Games thg_loser ON g.game_id = thg_loser.game_id AND thg_loser.team_id != thg_winner.team_id
JOIN Teams thg_winner_team ON thg_winner.team_id = thg_winner_team.team_id
JOIN Teams thg_loser_team ON thg_loser.team_id = thg_loser_team.team_id
JOIN Team_Stats ts ON ts.game_id = g.game_id AND ts.team_id = thg_loser.team_id
WHERE ts.penalty_yards > 30
ORDER BY ts.penalty_yards DESC;
```
### Results 
| game_id | game_date  | venue_name           | losing_team        | penalty_yards | winning_team          |
|---------|------------|----------------------|--------------------|---------------|-----------------------|
| 5       | 2024-12-07 | Mercedes-Benz Stadium | Texas Longhorns    | 45            | Georgia Bulldogs      |


---

# Complexity 

| Feature                          | Q1       | Q2       | Q3       | Q4        | Q5       | Q6        | Q7       | Q8       | Q9        | Q10       |
|----------------------------------|---------|---------|---------|----------|---------|----------|---------|---------|----------|----------|
| Joins Multiple Tables           | 4 tables | 2 tables | 3 tables | 2 tables | 3 tables | 6 tables | 2 tables | 2 tables | 7 tables | 6 tables |
| Aggregation (e.g., SUM, COUNT)  | -       | SUM     | -       | -        | -       | -        | -       | -       | -        | -        |
| Conditional Logic (e.g., WHERE) | WHERE   | -       | WHERE   | WHERE    | WHERE   | WHERE    | -       | WHERE   | WHERE    | WHERE    |
| Grouping (e.g., GROUP BY)       | -       | GROUP BY | -       | -        | -       | -        | -       | -       | -        | -        |
| Sorting (e.g., ORDER BY)        | ORDER BY | ORDER BY | -       | ORDER BY | ORDER BY | -        | ORDER BY | ORDER BY | -        | ORDER BY |
| Limiting Results (e.g., LIMIT)  | LIMIT   | -       | -       | -        | LIMIT   | -        | LIMIT   | -       | -        | -        |
| Subqueries                      | -       | -       | -       | Correlated | -       | -        | -       | -       | -        | -        |
| Multiple Joins to Same Table    | -       | -       | -       | -        | -       | Yes (2x) | -       | -       | Yes (3x) | Yes (2x) |
| Query Complexity            | Simple  | Simple  | Simple  | Complex   | Simple  | Complex  | Simple  | Simple  | Complex  | Complex  |









