# ⚽ Premier League 15/16 Tactical Analysis: Vertical Transition Velocity (VTV)

## 📌 Project Overview
This project analyzes the tactical landscape of the 2015/2016 English Premier League season by introducing and calculating a custom metric: **Vertical Transition Velocity (VTV)**. Using raw event data from StatsBomb, this analysis moves beyond basic possession stats to quantify *how fast* teams attack and transition the ball up the pitch.

## ⚡ What is VTV?
**Vertical Transition Velocity (VTV)** is a custom metric designed to measure the true speed of a team's attack. It is calculated as:
**VTV = Progression Distance (x-axis) / Duration of Possession (Seconds)**

### Why is VTV Important and Different?
Traditional metrics like "Total Attacks" or "Possession %" are flawed. A team can hold the ball for 5 minutes passing sideways without creating a threat. VTV ignores stagnant possession. By filtering out non-progressive plays and defensive clearances, VTV explicitly measures the speed and intent of a team's forward movement. It separates teams that rely on slow positional play from those that exploit rapid transitions.

## 🦊 Why Leicester City 15/16?
Leicester City's 15/16 title win is the ultimate anomaly in modern football. They won the hardest league in the world with historically low possession stats. How? Through lethal, clinical counter-attacks. They are the perfect benchmark for this project. If the VTV logic is sound, Leicester must empirically stand out as the ultimate transition team in the dataset.

## 📊 VTV Scores & Team Rankings

![VTV Bar Chart](https://raw.githubusercontent.com/fadhilra101/vertical-transition-velocity/main/vtv_rankings_bar_chart.png)

At first glance, teams like Norwich (8.70) and Watford (8.60) topped the average VTV charts, with Leicester City ranking 6th (8.16). However, deeper validation revealed a classic **Sample Size Bias**. 

![Scatter Plot](https://raw.githubusercontent.com/fadhilra101/vertical-transition-velocity/main/leicester_counter_attack_map_clean.png)

When plotting VTV against the *Volume* of Counter-Attacks:
* **The Outliers:** Norwich and Watford had high speeds but low volumes (~80 attacks). Their average was skewed by a few long-ball anomalies.
* **The Benchmark:** Leicester City executed a staggering **116 valid counter-attacks** (highest in the league) while maintaining an elite average VTV of 8.16. This proves their tactic was a consistent, deliberate system, not a statistical fluke.

## 🧠 Tactical Implications (The Mind of the Game)
In tactical terms, high VTV signifies a team's ability to exploit disorganized defensive structures. 
* A team with **High VTV & High Volume** (Leicester) thrives on drawing the opponent in, winning the ball, and punishing them before their defensive block can reset. 
* Conversely, teams with **Low VTV** (like Arsenal or Man City in this dataset) rely on *Slow Build-up*, preferring to break down set defenses through sustained pressure and intricate passing rather than raw speed.

## 🛠️ Methodology & Edge Case Handling
To ensure data accuracy and reflect realistic football logic, the raw StatsBomb event data was aggressively cleaned:
1. **Timestamp Normalization:** Addressed chronological grouping issues inherent in the API.
2. **Clearance Exclusion:** Removed defensive clearances and panic kicks that artificially inflated progression distance.
3. **Minimum Duration:** Filtered out possessions under 4 seconds to eliminate meaningless goal kicks and focus purely on tactical build-ups and carries.
