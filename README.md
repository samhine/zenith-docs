# Zenith

# Introduction

Zenith is a user friendly Google Sheets add-on for interacting with the Riot API. This project is currently in it's infancy, so feedback/suggestions are greatly appreciated. Zenith currently is given on a per-user basis and is not open source (though this _may_ change in the future).

To use Zenith, you will your own Riot API key. To do this, follow the "Get Started" section of [this official Riot documentation](https://developer.riotgames.com/docs/portal).

# Set up

To get started you will need to create a `Credentials` tab within your sheet to which Zenith is connected. Then place;

- your chosen region/platform in cell _A2_. You can find a list of supported regions [here](https://developer.riotgames.com/docs/lol#_routing-values).
- your Riot API key in cell _B2_. Zenith stores your API key to be sent off with your requests - it is _never_ stored persistently.

You may change either of these values at any time.

# Methods

Zenith adds custom functions to your sheets environment. They behave similarly to built in sheets functions such as `=SUM()` or `=VLOOKUP()`. Documentation for all user facing Zenith methods are included in tooltips that appear while typing methods.

## getAccountIdBySummoner(summoner_name)

Retrieves account ID for a given summoner name.

**Parameters**

**summoner_name**: `text`, Name of summmoner.

**Returns**: `text`, Account ID for provided summoner name.

## getSummonerByAccountId(account_id)

Retrieves summmoner name for a given account ID.

**Parameters**

**account_id**: `text`, Account ID of summmoner.

**Returns**: `text`, Summoner name for provided account ID.

## getChampionListForMatch(match_id, side)

Champion list for given match. If side is undefined, all champions are returned with blue side champions listed first.

**Parameters**

**match_id**: `text`, ID of match

**side**: `text | undefined`, Side for which champions will be returned ("blue" or "red")

**Returns**: `range`, List of champions for given match.

## getSummonerListForMatch(match_id, side)

Summoner list for given match. If side is undefined, all summoners are returned with blue side summoners listed first. Note, this method will NOT work for custom games since indentity information is not given by the API.

**Parameters**

**match_id**: `text`, ID of match

**side**: `text | undefined`, Side for which summoners will be returned ("blue" or "red")

**Returns**: `range`, List of summoners for given match.

## getStatForChampion(match_id, champion_name, statistic)

Parses match for chosen statistic and returns it for given champion.

**Parameters**

**match_id**: `text`, Parses match for chosen statistic and returns it for given champion.

**champion_name**: `text`, Parses match for chosen statistic and returns it for given champion.

**statistic**: `text`, Parses match for chosen statistic and returns it for given champion.

**Returns**: `text`, Statistic for champion in provided match.

## getStatForSummoner(match_id, summoner_name, statistic)

Parses match for chosen statistic and returns it for given summoner.

**Parameters**

**match_id**: `text`, Parses match for chosen statistic and returns it for given summoner.

**summoner_name**: `text`, Parses match for chosen statistic and returns it for given summoner.

**statistic**: `text`, Parses match for chosen statistic and returns it for given summoner.

**Returns**: `text`, Statistic for summoner in provided match.

# Avalible Statistics

| Statistic    | Description                                                        | Timeline Available? |
| ------------ | ------------------------------------------------------------------ | ------------------- |
| gold         | Gold for a champion/summoner                                       | Yes.                |
| cs           | Minions + Jungle minions killed for a champion/summoner            | Yes.                |
| kills        | End game kills for a champion/summoner                             |                     |
| deaths       | End game deaths for a champion/summoner                            |                     |
| assists      | End game assists for a champion/summoner                           |                     |
| goldPerMin   | (total gold / game duration in minutes) for a champion/summoner.   |                     |
| csPerMin     | (total cs / game duration in minutes) for a champion/summoner.     |                     |
| damage       | End game damage dealt to enemy champions for a champion/summmoner. |                     |
| damagePerMin | (total damage / game duration in minutes) for a champion/summoner. |                     |
| kda          | "kills/deaths/assists" for a champion/summoner.                    |                     |
| kdr          | (kills + assists / deaths) for a champion/summoner.                |                     |

# Best Practices

Although rate limiting is built in to Zenith, there are some ways _you_ can limit the chance of throttling your project;

- Once you have gathered data that need not change (or make extra calls to Zenith), copy this data and _paste as value_. This prevents cells from spamming Zenith and consequently the API when that data doesn't actually need to be updated.
- Limit cell dependancies. This means that you have as few cells as possible waiting for another cell to load. Pass by value wherever possible, rather than by cell.

# Contributors and Contacts

- Sam Hine

  - [twitter.com/samhine](http://twitter.com/samhine)
  - sam.hine27 (at) gmail.com

- Chris Georgiou
