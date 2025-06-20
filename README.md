# MMM-OpeningHours - WIP

A [MagicMirror²](https://magicmirror.builders) module to show store opening hours.

[![Platform](https://img.shields.io/badge/platform-MagicMirror-informational)](https://MagicMirror.builders)

[![Known Vulnerabilities](https://snyk.io/test/github/Menturan/MMM-OpeningHours/badge.svg)](https://snyk.io/test/github/mumblebaj/MMM-OpeningHours)
[![Yarn](https://img.shields.io/badge/dependency%20manager-Yarn-blue.svg?style=flat-square)](https://yarnpkg.com)
![Maintenance](https://img.shields.io/maintenance/yes/2025.svg?style=flat-square)
[![GitHub commit activity](https://img.shields.io/github/commit-activity/m/mumblebaj/MMM-OpeningHours.svg?style=flat-square)](https://github.com/mumblebaj/MMM-OpeningHours/graphs/commit-activity)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](LICENSE)


MagicMirror² module that displays places opening hours.
Relies on [Google Places API](https://developers.google.com/places/web-service/intro).

## Screenshot
![Screenshot](screenshot.png)

## Prerequisite

You need to have a Google Places API key to use this module.
Follow their guide here: [Get API Key](https://developers.google.com/places/web-service/get-api-key).

**NOTE! The opening hours field in Google Places API is a billed field.
However, Google give you a free monthly credit.
Please carefully read about their billing [here](https://developers.google.com/places/web-service/usage-and-billing).
Contributors of this module is not responsible for any charges.**

## Install
This module uses Yarn.
1. `yarn install` <br>
NPM also works
2. `npm install --omit=dev`

## Find places ID
Search for the place to get its ID. You really needs to **search** for a place. Clicking on a place wont cut it.

[Place ID Finder](https://developers.google.com/maps/documentation/javascript/examples/places-placeid-finder)

## Configuration

| Key          | Value             | Required | Default           | Description                                                                                                                                                                                             |
|--------------|-------------------|----------|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| googleApiKey | _string_          | Yes      | N/A               | Your Google Places API Key.                                                                                                                                                                             |
| places       | [See below.](#places-config)        | Yes      | N/A               | List of place ids. [See above.](#find-places-id)                                                                                                                                                        |
| scheduleTime | _milliseconds_    | No       | 86400000 (24h)    | Time between fetching place data from Google.                                                                                                                                                           |
| timeFormat   | _number_          | No       | config.timeFormat | 24h, 12h. If not specified, uses same as parent config.                                                                                                                                                 |
| language     | _ISO 639-1  code_ | No       | config.language   | Changes the translation. Time and date is still locale. Two letter country code. [ISO 639-1 code](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes). If not specified, uses same as parent config. |
| styling      | _object_          | No       | See next table.   | Configure table style.
| debug        | _boolean_         | No       | false             | Debug output.                                                                                                                                                                                           |
| mockData     | _boolean_         | No       | false             | Fake API-call. Used for development.                                                                                                                                                                    |

### Places config
Places are provided as a list `[]`. Example - `["place_id_1", "place_id_2", "place_id_3"]`.

If you would like to use an alias for a place you put the place id and the alias in a list with the **place id first**. Example - `["place_id_1", ["place_id_2", "Place 2"], "place_id_3"]`.

#### Styling

| Key           | Value     | Required | Default | Description                                                           |
|---------------|-----------|----------|---------|-----------------------------------------------------------------------|
| showTimeUntil | _boolean_ | No       | false   | Show time until close/open instead of time when closed/open.          |
| textAlign     | _string_  | No       | center  | Table text alignment. Possible values: left, right, center.           |
| size          | _string_  | No       | small   | Size of table. Possible values: xsmall, small, medium. large, xlarge. |


## Example config

```
{
    module: "MMM-OpeningHours",
    position: "bottom_right",
    header: "Opening hours",
    config: {
    googleApiKey: "XXXXXXXXXXXXXX",
        places: ["xxxxxxxx", ["yyyyyyyy", "Alias y"]],
        styling: {
          size: 'small'
        }
    }
}
```
## Development
This module isn't perfect. If you find a bug or has a feature request don't hesitate to create an issue OR even better, create a pull request! :D
