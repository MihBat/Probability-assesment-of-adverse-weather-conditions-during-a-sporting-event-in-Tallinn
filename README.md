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

## Methodoogy
Short-term seven-day weather forecasts, which are more accurate, are typically used, but July is still two weeks away. Therefore, in addition to using short-term forecasts, it is proposed to use historical weather data analysis for July in Tallinn as an additional decision-making tool.

The following data were used for the statistical analysis:
- Open Meteo archived weather data for Tallinn; from July 1 to 20, 2010-2024 `data/tln_weather_july_2010_2024.csv`
- The following parameters were selected from the archive: precipitation, wind speed, temperature, and atmospheric pressure.

P. S. More methodogy description in `code/weather_cond_analysis.ipynb`

## Workflow
