# tzif-data

Automatically build and publish compiled IANA time zone data files in TZif (`zoneinfo`) format.

This repository provides static URLs for downloading individual compiled time zone files, for example:

- https://nicolasbon.net/tzif-data/zoneinfo/Europe/Amsterdam
- https://nicolasbon.net/tzif-data/zoneinfo/America/New_York
- https://nicolasbon.net/tzif-data/zoneinfo/Etc/UTC

## What this repository does

The GitHub Actions workflow:

1. Downloads the latest IANA `tzdata` archive.
2. Extracts the time zone source files.
3. Compiles them with `zic` into binary TZif files.
4. Copies the compiled `zoneinfo` tree into a GitHub Pages artifact.
5. Deploys the files to GitHub Pages.

The generated files are suitable for software that can read standard TZif files.

## Why

Some environments, especially embedded systems, browsers, static clients, or small custom runtimes, may not have a local `/usr/share/zoneinfo` database available.

This project makes it possible to fetch a compiled time zone file directly over HTTP from a static host.

## Data source

The data comes from the IANA Time Zone Database, also known as `tz` or `zoneinfo`.

IANA publishes time zone rules and historical offset data for representative locations around the world. The database is updated periodically when political bodies change UTC offsets, daylight-saving rules, or time zone boundaries.

## Notes

- This repository does not define time zone rules itself.
- It republishes compiled output from the upstream IANA time zone database.
- Consumers should treat the generated files as data files, not as an API with stability guarantees beyond the normal IANA zone names and aliases.
- If exact reproducibility matters, pin to a specific generated commit rather than relying on the latest deployment.

## License

This repository’s workflow and documentation are dedicated to the public domain under CC0-1.0.

The generated TZif files are compiled from the IANA Time Zone Database. The upstream tzdb data is public domain unless otherwise specified by IANA.
