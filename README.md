# nhl-api-py-examples
A collab notebook of the nhl-api-py package.


```python
pip install nhl-api-py
```

    Collecting nhl-api-py
      Downloading nhl_api_py-0.1.3-py3-none-any.whl (5.4 kB)
    Collecting httpx
      Downloading httpx-0.24.1-py3-none-any.whl (75 kB)
         ---------------------------------------- 0.0/75.4 kB ? eta -:--:--
         ---------------------------------------- 75.4/75.4 kB 4.1 MB/s eta 0:00:00
    Requirement already satisfied: certifi in c:\users\cscha\anaconda3\envs\generic-ml-env\lib\site-packages (from httpx->nhl-api-py) (2023.5.7)
    Collecting httpcore<0.18.0,>=0.15.0
      Downloading httpcore-0.17.2-py3-none-any.whl (72 kB)
         ---------------------------------------- 0.0/72.5 kB ? eta -:--:--
         ---------------------------------------- 72.5/72.5 kB ? eta 0:00:00
    Requirement already satisfied: idna in c:\users\cscha\anaconda3\envs\generic-ml-env\lib\site-packages (from httpx->nhl-api-py) (3.4)
    Requirement already satisfied: sniffio in c:\users\cscha\anaconda3\envs\generic-ml-env\lib\site-packages (from httpx->nhl-api-py) (1.2.0)
    Collecting h11<0.15,>=0.13
      Downloading h11-0.14.0-py3-none-any.whl (58 kB)
         ---------------------------------------- 0.0/58.3 kB ? eta -:--:--
         ---------------------------------------- 58.3/58.3 kB ? eta 0:00:00
    Requirement already satisfied: anyio<5.0,>=3.0 in c:\users\cscha\anaconda3\envs\generic-ml-env\lib\site-packages (from httpcore<0.18.0,>=0.15.0->httpx->nhl-api-py) (3.5.0)
    Installing collected packages: h11, httpcore, httpx, nhl-api-py
    Successfully installed h11-0.14.0 httpcore-0.17.2 httpx-0.24.1 nhl-api-py-0.1.3
    Note: you may need to restart the kernel to use updated packages.
    


```python
from nhlpy import NHLClient
```

### Getting Started - Create the NHLClient


```python
client = NHLClient()
```

### Team APIs


```python
teams = client.teams.all()
teams
```


```python
buffalo = client.teams.get_by_id(id=7)
buffalo
```


```python
next_buffalo_game = client.teams.get_team_next_game(id=7)
next_buffalo_game
```


```python
prev_buffalo_game = client.teams.get_team_previous_game(id=7)
prev_buffalo_game
```


```python
buffalo_with_stats = client.teams.get_team_with_stats(id=7)
buffalo_with_stats
```


```python
buffalo_roster = client.teams.get_team_roster(id=7)
buffalo_roster
```


```python
buffalo_full_team_stats = client.teams.get_team_stats(id=7)
buffalo_full_team_stats
```

### Standing APIs


```python
# These can be used in conjunction with get_standings_by_standing_type
all_standing_types = client.standings.get_standing_types()
all_standing_types
```


```python
# standings by season
all_standings = client.standings.get_standings(season="20222023", detailed_record=False)
all_standings
```


```python
# same as above but with more detailed information
# standings by season
all_standings = client.standings.get_standings(season="20222023", detailed_record=True)
all_standings
```


```python
# Get standings by type, types can be found via get_standings_by_type, or in the docstring
post_season = client.standings.get_standings_by_standing_type(standing_type="regularSeason")
post_season
```


```python

```

### Players


```python
# APIs to access player information.  Requires person_id, found from `teams.get_team_roster()`
jj = client.players.get_player(person_id=8482175)
jj
```


```python
jj_stats = client.players.get_player_stats(person_id=8482175, season="20222023", stat_type="statsSingleSeason")
jj_stats
```


```python
# Differnt stat types you can access
types = client.players.get_player_stat_types()
types
```


```python

```
