# hk-pmtiles-generation
Github Action to generate Hong Kong PMTiles every few days automatically and publish to Github Pages, and (optionally) Cloudflare R2

## Usage
Fork this repo, setup GitHub pages and make sure you have Actions enabled :)
You might also want to use https://github.com/marketplace/actions/keepalive-workflow to keep your fork alive, preventing the scheduled actions from being disabled

### Cloudflare R2 (Optionally)

To host the tiles in Cloudflare R2, it is required to set the below secrets for the forked repository following the [Github instructions](https://docs.github.com/en/actions/how-tos/write-workflows/choose-what-workflows-do/use-secrets).

| Name | Description |
|---|---|
|R2_ACCOUNT_ID| Your Cloudflare account ID.|
|R2_ACCESS_KEY_ID | Your Cloudflare R2 bucket access key ID. |
|R2_SECRET_ACCESS_KEY | Your Cloudflare R2 bucket secret access key. |
|R2_BUCKET | Your Cloudflare R2 bucket name. |

## Attribution

The tilesets that power the generated PMTiles are Produced Works of the OpenStreetMap dataset under the Open Database License. Web maps and native apps that use this Produced Work must visibly attribute © OpenStreetMap - for example, in the corner of the map display.

## Disable generation of a specific type
### For manual workflow runs:
When manually triggering the workflow, uncheck any of these options:
- Build vector tiles
- Build labels tiles
- Build raster light tiles
- Build raster dark tiles

### For scheduled runs:
Set repository variables in Settings → Secrets and variables → Actions → Variables:
- `CRON_BUILD_VECTOR`
- `CRON_BUILD_LABELS`
- `CRON_BUILD_RASTER_LIGHT`
- `CRON_BUILD_RASTER_DARK`

If variables are not set, all tile types will be generated

## Styles

The default styles are adopted from Protomaps with slight modifications so it looks better in lower resolutions.

You may adjust the styles by modifying the files `render-style.json` and `render-style-dark.json`.