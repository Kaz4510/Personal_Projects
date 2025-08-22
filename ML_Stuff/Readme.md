<h1>What is League of Legends</h1>
  
<p>League of Legends (LoL) is a multiplayer online battle arena (MOBA) video game developed by Riot Games. Released in 2009, it’s one of the most popular esports titles worldwide. In the game, two teams of five players compete to destroy the opposing team’s “Nexus,” a structure located in their base.
<br>
Each player controls a unique “champion” with distinct abilities, and gameplay combines strategy, teamwork, and fast-paced mechanics. Matches involve managing resources, controlling map objectives, and engaging in tactical battles. Beyond the game, League of Legends has grown into a global esports ecosystem with professional leagues, massive tournaments like the World Championship, and a strong cultural impact through music, animation, and community events.</p>

<h2>Glossary:</h2>
<ul>
<li>Warding totem: An item that a player can put on the map to reveal the nearby area. Very useful for map/objectives control.</li>
<li>Minions: NPC that belong to both teams. They give gold when killed by players.</li>
<li>Jungle minions: NPC that belong to NO TEAM. They give gold and buffs when killed by players.</li>
<li>Elite monsters: Monsters with high hp/damage that give a massive bonus (gold/XP/stats) when killed by a team.</li>
<li>Dragons: Elite monster which gives team bonus when killed. The 4th dragon killed by a team gives a massive stats bonus. The 5th dragon (Elder Dragon) offers a huge advantage to the team.</li>
<li>Herald: Elite monster which gives stats bonus when killed by the player. It helps to push a lane and destroys structures.</li>
<li>Towers(Turret): Structures you have to destroy to reach the enemy Nexus. They give gold.</li>
<li>Level: Champion level. Start at 1. Max is 18.</li>
</ul>


Dataset: https://www.kaggle.com/datasets/bobbyscience/league-of-legends-diamond-ranked-games-10-min

League of legends guide: https://www.leagueoflegends.com/en-us/how-to-play/

Content

This dataset contains the first 10min. 10k ranked games(solo queue) from a high mmr(diamond 1 to master).

Each game is unique and there is no missing value.

<ul>Columns:
<li>gameId : Unique Riot ID of the game</li>
<li>blueWins : target column (1:blue team won, 0: red team won)</li>
<li>xxWardsPlaced: Number of warding totems placed by xx(blue/red) team</li>
<li>xxWardsDestroyed: Number of enemy warding totems</li>
<li>xxFirstBlood: First kill of the game (1:blue team did, 0: red team did)</li>
<li>xxKills: Number of enemies killed</li>
<li>xxDeaths: Number of deaths</li>
<li>xxAssists: Number of kill assits</li>
<li>xxEliteMonsters: Number of elite monsters(Dragons and Heralds) killed</li>
<li>xxDragons: Number of dragons killed</li>
<li>xxHeralds: Number of heralds killed</li>
<li>xxTowersDestroyed: Number of structures destroyed</li>
<li>xxTotalGold: Total gold</li>
<li>xxAvgLevel: Average champion level</li>
<li>xxTotalExperience: Total experience</li>
<li>xxTotalMinionsKilled: Total minions killed (CS)</li>
<li>xxTotalJungleMinionsKilled: Total jungle monsters killed</li>
<li>xxGoldDiff: Gold difference compared to the enemy team</li>
<li>xxExperienceDiff: Experience difference compared to the enemy team</li>
<li>xxCSPerMin: CS per minute</li>
<li>xxGoldPerMin: Gold per minute</li>
</ul> 

<h3>Pairwaise Distribution:</h3>
<img width="2988" height="3393" alt="image" src="https://github.com/user-attachments/assets/59704ffd-1223-4e15-85aa-1c00ea311778" />


<h3>Feature Importance</h3>
<img width="680" height="633" alt="image" src="https://github.com/user-attachments/assets/67b35986-d89c-4cba-8ca7-abee7ba77536" />
