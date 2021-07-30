# Highcharts Node.js Export Server (co2m-chart-exporting)
====

## Purpose
Our own version of the Highcharts Node.js Export Server which we self-host (so no privacy/confidentiality issues) and isn't rate limited.
We use this in SmartTrackers Measurements for two reasons:

- To convert charts in Reports to a static SVG image. This makes sure we do not need Highcharts JavaScript in the PDF conversion, which caused various problems (and doesn't work with new Highcharts versions). It also makes sure that what the user sees when editting the report, is the same as what is included in the PDF.
- To let users of our app download an image (PNG, JPEG, PDF or SVG) of a single chart he sees (for example on the dashboard).

## Run (locally)
1. Install Node.js and NPM: on MacOS `brew install node`
2. Install the package/depencies: `npm install`
3. Start the server: `npm start`
4. The export server is now available on: http://localhost:7801. This URL can be set in the [Highcharts exporting options](https://api.highcharts.com/highcharts/exporting.url).

## Update
To update the export server perform the following steps:
1. Increase the version number for the highcharts-export-server dependency in [package.json](package.json#L8)
2. Increase the version number for Highcharts in the HIGHCHARTS_VERSION ENV var in the install command in [package.json](package.json#L4). This version should match the [version of Highcharts used by Measurements!](https://github.com/CO2Management/co2m/blob/develop/yarn.lock)
3. Install the new dependencies: `npm install`
4. If needed update the config for the server, found in [options.json](options.json)

## Deploy (to Heroku)
1. Deploy your branch to staging through the Heroku web interface (using the GitHub link): https://dashboard.heroku.com/apps/co2m-chart-exporting-staging/deploy/github
2. Create a PR with your changes. Make sure it's reviewed, tested (on staging) and merged (to master).
3. Deploy the new master branch through the Heroku web interface: https://dashboard.heroku.com/apps/co2m-chart-exporting/deploy/github
