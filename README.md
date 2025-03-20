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

# Key Entities
1. **Games**: Stores details about each game, including the game ID, date, and scores for both teams. This entity helps track when and where games were played and their final results.  
2. **Teams**: Contains information about each football team, including the team name and conference. This is useful for understanding team backgrounds and historical performance.  
3. **Players**: Maintains records of individual players, including their names, team affiliation, position, height, weight, and jersey number.  
4. **Team_Stats**: Holds team-level performance metrics, such as passing yards, rushing yards, and penalties for each game.  
5. **Player_Stats**: Tracks individual player statistics per game, including passing yards, rushing yards, receiving yards, touchdowns, tackles, and interceptions.  
6. **Penalties**: Records penalty details such as type, yards lost, and the player and team responsible.  
7. **Injuries**: Documents player injuries, including descriptions and status updates.  
8. **Recruiting**: Lists new recruits, including their first name, last name, committed team, and star rating.  
9. **Coaches**: Stores details about team coaches, including first name, last name, position, and years of experience.  
10. **Conferences**: Contains details about different football conferences, such as conference name and abbreviation.  
11. **Teams_has_Games**: Establishes the relationship between teams and games, linking each team to the specific games they have played.  
12. **Venues**: Captures information about where games are played, including venue name and state.

# Data Model
<img width="700" alt="image" src= "https://github.com/user-attachments/assets/cb287cc5-0321-4dd1-9bd8-74bcd3a3dc7c" />

# Data Dictionary
![image](https://github.com/user-attachments/assets/352f02fe-e7c2-4d78-b780-52eeb5ef6360)

![image](https://github.com/user-attachments/assets/2f8d4e31-bb2d-418d-b66d-ea1a21b85efe)

![image](https://github.com/user-attachments/assets/09425b12-3285-4568-87cc-9acc4a5497c6)

![image](https://github.com/user-attachments/assets/49157efc-737b-4c0e-bf59-2dcb51091a13)

![image](https://github.com/user-attachments/assets/4638a7a5-fd9a-4076-bdcd-7517f2d070f5)

# Queries 
## First Query
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

---
## Second Query 
```sql
SELECT t.team_name, SUM(ts.penalty_yards) AS total_penalty_yards, SUM(ts.penalties) AS total_penalties
FROM Team_Stats ts
JOIN Teams t ON ts.team_id = t.team_id
GROUP BY t.team_id, t.team_name
ORDER BY total_penalty_yards DESC;
```

---
## Third Query 
```sql
SELECT p.first_name, p.last_name, t.team_name, i.injury_desc, i.injury_status
FROM Injuries i
JOIN Players p ON i.player_id = p.player_id
JOIN Teams t ON p.team_id = t.team_id
WHERE i.game_id = 5;
```

---
## Fourth Query 
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

---
## Fifth Query 
```sql
SELECT p.first_name, p.last_name, t.team_name, ps.tackles
FROM Player_Stats ps
JOIN Players p ON ps.player_id = p.player_id
JOIN Teams t ON p.team_id = t.team_id
WHERE ps.game_id = 5 AND ps.tackles > 0
ORDER BY ps.tackles DESC
LIMIT 1;
```

---
## Sixth Query 
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

---
## Seventh Query 
```sql
SELECT c.first_name, c.last_name, t.team_name, c.position, c.years_experience
FROM Coaches c
JOIN Teams t ON c.team_id = t.team_id
ORDER BY c.years_experience DESC;
```

---
## Eigth Query 
```sql
SELECT p.first_name, p.last_name, t.team_name, p.position, p.class_year
FROM Players p
JOIN Teams t ON p.team_id = t.team_id
WHERE p.class_year = 'Senior'
ORDER BY t.team_name, p.last_name;
```

---











