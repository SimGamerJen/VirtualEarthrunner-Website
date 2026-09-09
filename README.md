# Virtual Earthrunner IT website

Responsive static website draft for virtualearthrunner.com. Red, charcoal and silver branding uses the supplied historic logo artwork, presented with CSS clipping to omit the former company wording. The source image is embedded unchanged in the HTML; no external assets, scripts, fonts, analytics or form services are loaded.

## Local review

Run `python -m http.server 8080 --directory public` from this repository, then open http://localhost:8080. No build is needed. Cloudflare applies `public/_headers` when deployed; the local Python server does not.

## Cloudflare alongside SimGamerJen

Create a separate Worker named `virtualearthrunner-website` in the existing Cloudflare account. Connect this repository, selecting the draft branch for review or main after merging. Leave the build command blank and use `npx wrangler deploy` as the deploy command, from the repository root. Wrangler serves only `public/`.

This is independent of the `simgamerjen-website` Worker and its download database. Do not copy its bindings or change its domain routes.

After review, add virtualearthrunner.com as an active zone in the same Cloudflare account if it is not already there. On this Worker, use Settings > Domains & Routes > Add > Custom Domain to attach virtualearthrunner.com. Attach www.virtualearthrunner.com too if wanted. Review any existing DNS records for conflicts; preserve email records. Neither domain is attached automatically by this draft configuration.

## Before public launch

- Enquiries use the confirmed info@virtualearthrunner.com address through an email button and visible address link.
- Review service descriptions and biography; no availability, qualifications, client endorsements or current company registration are claimed.
- Confirm the current legal trading details for the footer as applicable.
- Remove the noindex meta tag, change robots.txt to permit indexing and remove the draft footer label when approved for launch.
- This draft has no contact form or tracking. Revisit privacy information if those are introduced.

Cloudflare references: https://developers.cloudflare.com/workers/configuration/routing/custom-domains/ and https://developers.cloudflare.com/workers/static-assets/get-started/
