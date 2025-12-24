# Home-Assistant-Radio-Explorer
A WIP set of automations and commands for adding complexity to Radio Browser functions in Home Assistant

I like services such as [radio.garden](radio.garden) that help explore the world and discover audio from around the world. This set of scripts adds some simple functionality to Home Assistant, based on the [Radio Browser API](https://de2.api.radio-browser.info/). This is a series of REST commands that have been designed to retrieve a single random radio station based on given criteria. It is tied into automations around the conversation triggers (i.e. Voice assistant).

If you have a Voice Assistant configured in your HA setup you can add the yaml script to your `packages` folder in the config directory, and adding these lines to `configuration.yaml`:
```
homeassistant:
  packages: !include_dir_named packages
```

Or, just investigate the YAML to see how I've set up the REST commands, and the automations, to adjust for your own situation. It is not complex, just took a while to refine so might serve a good starting point.

# Usage
In the default setup you can use the following voice commands:

## "Play random radio"
Finds and plays a random radio station from anywhere in the world. This can be anything, and is always surprising. The only downside is that the API caches your request, so if you ask for this a second time, without waiting very long, it will return the same station.

## "Play music from `country`"
As it sounds, but make sure to word the country like "Italy" and not "Italian", because the API only knows plain country names. However, many stations use the possessive country name in tags, so it can get picked up by the next request:

## "Play `genre` music" 
Again as it sounds, but it searches partial tags, so you can say "Play Psytrance Music" for example. Because it uses tags you can be creative here, because tags in Radio Browser can be weird. For example there is a tag "gothy gloomy synthy dancey stuff". See the [huge list of tags](https://de2.api.radio-browser.info/json/tags). As mentioned above, you can say "Play Korean music" to hear stations tagged with "korean", which usually gives good results (but technically does not include all stations in Korea, just the ones using that tag).

## "Play `genre` music from `country`"
This is a combination of both above. This is handy if you want to hear less generic pop music, by asking for "Play traditional music from Colombia", or "Play metal music from Finland".
