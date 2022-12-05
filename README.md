
# FM23 Similarity Score Testing
## **Goal**
> This analysis uses cosine similarity scoring based on Football Manager 23 attributes to 'predict' who a young player may emulate at full potential. Football Manager data seems to pass the smell test fot the most part in terms of it's accruacy relative to what's readily and publicly available. ([See this in action on my blog!](https://futek.io/))


## Data
>  I previously scraped player data from Football Manager 23-- **this includes over ~100 attributes for ~450 thousand players from around world:**
>>  Key attributes include:
>>>  Current & Potential ability

>>> Height, Preferred Foot, Position



>>> Attacking Attributes: 
>>>>>`['flair','off_the_ball', 'vision', 'crossing', 'dribbling', 'finishing', 'free_kicks', 'frist_touch', 'long_shots', 'passing']`

>>>  Defensive Attributes: 

>>>>>`['anticipation','positioning', 'acceleration', 'jumping_reach', 'pace', 'stamina', 'strength', 'heading', 'marking', 'tackling']`

## Methodology for Player Potential
> Leverage cosine similarities of the aforementioned attributes in addition to weighting methods for other attributes such a height, preffered foot, potential ability to 'predict' who a young player may emulate at full 
potential.

### Example

1) Take a given young player:

> Player A: 
>> Potential: `180`

>> Position: `AML`

>> Height: `5'10"`

>> Preferred Foot: `Right`

>> Sorted Attributes: `{"pace": 12, "dribbling": 11, "acceleration": "10", "passing": 10}`



2) Scan the database for players whof fit the following criteria in relation to Player A:
> Current Ability == += X (10,20, etc.) from Player A's Potential ability

> Same/similar Position


3) For all potential matches in terms of position and current ability, calculate a similarity score:
> Stack rank their attributes in relation to Player A's to calculate their cosine similarity:
>> Ex:

>>> Player A: `{"pace": 12, "dribbling": 11, "acceleration": "10", "passing": 10 etc...}`

>>> Player B: `{"acceleration": 12, "pace": 11, "dribbling": "10", "flair": 10 etc...}` 

>> Apply weights to other factors: `weights = {'c_weight': 1, 'c_height': 7, 'c_pref_foot': 7, 'c_ability': 35, 'c_comb': 50}`
>>> `c_ability`: `35%`
>>>> Similarity in Player A's Potential Ability to Player B's Current Ability

>>> `c_comb`: `35%`
>>>> Cosine similarity based on the aforementioned factors

>>> `c_height`: `7%`
>>>> Height similarity

>>> `c_pref_foot`: `7%`
>>>> Preferred foot similarity

>>> `c_weight`: `1%`
>>>> Weight similarity

4) Calculate the 'potential fit' by league
> Take all players 




4) Combine to calculate an overall similarity score for all potential matches:
> Calculate the Top 20 leagues based on Current Ability for players between the ages of 25-29 (in their "prime").
>> Calculate the percentile for which Player A's potential ability falls in per league

5) Output for a given player:
<img src="https://i0.wp.com/futek.io/wp-content/uploads/2022/12/Nicolas-Jackson__cover-1.png?w=964&ssl=1" style="height: 1000px;"/>
<img src="https://i0.wp.com/futek.io/wp-content/uploads/2022/12/Nicolas-Jason__similarity.png?w=1494&ssl=1" style="height: 1000px;"/>
<img src="https://i0.wp.com/futek.io/wp-content/uploads/2022/12/Nicolas-Jackson__strweak.png?w=1502&ssl=1" style="height: 1000px;"/>
