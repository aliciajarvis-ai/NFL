# SEC DATABASE
# Team Name: 
G2

# Team Members
1. Alicia Jarvis - https://github.com/aliciajarvis-ai
2. Oliver Schouest - https://github.com/oschouest
3. Tejas Panicker - https://github.com/Tejas5012
4. Nitya Kottapally - https://github.com/nityakottapally1

# Project Scenario
Alex Carter, a journalist covering NCAA Division I Football, is preparing a comprehensive wrap-up of the 2024 SEC season. With the season concluded, she wants to analyze the NFL draft picks from SEC teams, standout player performances, team trends, coaching changes, and other key developments within the conference. To ensure her article provides a unique and insightful perspective, she reaches out to a coworker for detailed SEC-specific data, including draft selections, player stats, team performance metrics, and notable off-season moves. By leveraging this information, Alex aims to craft an in-depth analysis that sets her apart in the competitive world of sports journalism.

# Key Entities
1. **Games**: Stores details about each game, including the game ID, date, location, and scores for both teams. This entity helps track when and where games were played and their final results.
2. **Teams**: Contains information about each football team, including team name, conference, home stadium, and founding year. This is useful for understanding team backgrounds and historical performance.
3. **Players**: Maintains records of individual players, including their names, team affiliation, position, height, weight, and status. This helps Alex analyze key players in the championship game.
4. **Team_Stats**: Holds team-level performance metrics, such as total yards, penalties, and penalty yards for each game. This allows for comparing team performances throughout the season.
5. **Player_Stats**: Tracks individual player statistics per game, including passing, rushing, and receiving yards, as well as touchdowns, tackles, and interceptions. This helps highlight standout players and their contributions.
6. **Penalties**: Records penalty details such as type, yards lost, and the player and team responsible. This helps Alex analyze discipline trends and how penalties impact game outcomes.
7. **Injuries**: Documents player injuries with descriptions and status updates. Knowing which key players are injured can be crucial for pre-game analysis.
8. **Recruiting**: Lists new recruits, including their high school, hometown, and committed team. This can provide insights into upcoming talent for teams.
9. **Coaches**: Stores details about team coaches, including names, roles, and experience levels. Coaching strategies can play a big role in game outcomes.
10. **Teams_has_Games**: Establishes the relationship between teams and games, linking each team to the specific games they have played.

# Data Model
<img width="323" alt="image" src="https://github.com/user-attachments/assets/42d2769b-207f-4751-ba30-26bdc8adb55f" />
