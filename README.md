# Probability assesment of adverse weather conditions during a sporting event in Tallinn

## Background
Let's assume that the organizers of a track cycling event to be held in mid-July 2025 (17-20 of July) in Tallinn are planning the preparation of spectator infrastructure taking into account possible weather conditions. Typically, protective structures (such as rain shelters) are provided for mass events, but in this case, their installation was not funded by the race sponsors.

As a result, the guests of honor, as well as other spectators, will be left without shelter in the event of a prolonged downpour. The organizers face a dilemma: rescheduling the event is no longer possible, there are no current weather forecasts for mid-July, and decisions regarding funding for the facilities for the guests of honor must be made by the end of June.

## Purpose
Therefore, organizers are faced with the task of assessing the likelihood of rain during the event.

The results of this analysis can be used to choose one of the following options:
- moving the event to an indoor venue (if possible)
- providing temporary shelters
- purchasing protective equipment (e.g., umbrellas)
- foregoing additional measures if the likelihood of precipitation is low.

## Methodology
Short-term seven-day weather forecasts, which are more accurate, are typically used, but July is still two weeks away. Therefore, in addition to using short-term forecasts, it is proposed to use historical weather data analysis for July in Tallinn as an additional decision-making tool.

The following data were used for the statistical analysis:
- Open Meteo archived weather data for Tallinn; from July 1 to 20, 2010-2024 `data/tln_weather_july_2010_2024.csv`
- The following parameters were selected from the archive: precipitation, wind speed, temperature, and atmospheric pressure.

P. S. More methodogy description in `code/weather_cond_analysis.ipynb`

## Workflow
Data processing 
- loading packages: requests, `pandas`, `urllib3`, `matplotlib`, `numpy`, `statsmodels`, and possibly `certifi`
- getting data: Open‑Meteo Archive API (Tallinn, July 1–20, 2010–2024, hourly).
- data preparation/cleaning

Analysis
- defining weather conditions: Long rain (≥1 mm/h, ≥3 h), long and strong wind (≥15 m/s, ≥3 h), and their combination.
- calculating probabilities: for each year (0/1) + 95% Wilson confidence intervals.
- comparing two periods – Event window (July 17–20) vs. seasonal window (July 1–20).

Visualization 
- probability of adverse weather conditions `probability_comparison.png`
- probability and 95% confidence interval (July 1–20, 2010–2024) `probabilities_with_ci.png`

## Results
**Event days (17-20 July):**
- Long rain (≥1 mm/h, ≥3h) during the event window is unlikely. Point estimate: **6.7%** (1 year out of 15). 95% CI: [1.2%, 29.8%].
- Strong wind (≥15 m/s, ≥3h) during the same four days is very common. Point estimate: **86.7%** (13 years out of 15). 95% CI: [62.1%, 96.3%].
- Combined: No simultaneous occurrence of long rain and strong wind was observed in the 17–20 July window over the 15‑year period. Probability **0.0%** (95% CI: [0.0%, 20.4%]).

**Mid-summer (1-20 July):**
- Long rain (≥1 mm/h, ≥3 h) during the 20‑day period is common. Point estimate: **73.3%** (11 years out of 15). 95% CI: [48.0%, 89.1%].
- Strong wind (≥15 m/s, ≥3 h) is almost guaranteed. Point estimate: **100%** (15 years out of 15). 95% CI: [79.6%, 100%].
- Combined: Simultaneous occurrence of long rain and strong wind was observed in 6 out of 15 years. Point estimate: **40.0%**. 95% CI: [19.8%, 64.3%].

## Conclusions
Weather in July in Tallinn is generally warm with occasional rain. While prolonged rainfall events are relatively common over the broader period (July 1–20), their probability during the specific event dates (July 17–20) remains low.

This highlights the importance of temporal scale: adverse conditions may occur during the month, but are unlikely to coincide with the exact event days.

Nevertheless, statistical analysis shows that the **true probability of rain in July is still high**, as shown by the confidence interval, so the **use of canopies for guests of honor is very recommended**. However, canceling an event due to a lack of canopies is not recommended; umbrellas can be purchased as a last resort.

## Possible next steps of analysis
For a more accurate weather assessment/forecast, it's it might be useful to **study weather patterns**, as the movement of cold and wet atmospheric fronts depends on pressure, wind speed, and direction, and to **apply machine learning methods (RF, etc.) to forecast the weather**.
