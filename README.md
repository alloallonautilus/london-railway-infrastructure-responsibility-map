# Greater London Railway Map — Final Clean Edition

This is the final clean-up of the existing Greater London Railway Map (v24 baseline), not the proposed new organisational atlas.

## Changes
- Removed Clapham-specific study-area navigation and endpoint/topology audit controls and code.
- Removed specialist route-assignment QA controls and associated downloads.
- Removed the special Clapham Junction shortcut from the live infrastructure section.
- All 20 bundled reference station markers now use a consistent symbol; these 20 are **not** a complete inventory of London stations.
- The optional OpenStreetMap detailed infrastructure loader applies uniformly to all viewed areas of London, including mapped station buildings, platforms and entrances, subject to coverage and live service availability.
- Preserved the 42-polygon bundled Thames candidate layer, archived route and region geometry, and archived railway centreline network.

## Publish
Upload `index.html`, `railway-data.js`, and `thames-osm-candidates.geojson` to the **root** of the existing GitHub Pages repository, replacing the corresponding files. No audit GeoJSON or CSV files are required. Allow GitHub Pages to rebuild and refresh the page.

## Source and limitations
Archived Network Rail GIS geometry is not authoritative for current organisational responsibilities. The bundled station markers are approximate, and detailed station footprints are requested live from OpenStreetMap only after enabling infrastructure at sufficient zoom. Thames geometry is user-provided OSM-derived data; visual continuity was reported satisfactory by the user, but complete cartographic accuracy has not been independently certified. OSM attribution: © OpenStreetMap contributors (ODbL).

Leaflet JavaScript and CSS are fetched from a CDN, and live detailed infrastructure requires Overpass access.


## Station symbols (final cartographic update)

- Principal central London termini use a larger white ring with dark centre dot; other bundled station markers use a smaller white ring.
- Principal terminus labels appear from zoom 10; other bundled station labels appear from zoom 13.
- This release **does not add every Greater London station**: the underlying bundled dataset still contains 20 approximate station positions. All detailed OSM station assets remain optional live data.
- Classification is for map readability, not a statement about station ownership or Network Rail managed-station status.


## Greater London stations (NaPTAN)

The map now includes **339 unique station-name markers** consolidated from **549 active NaPTAN railway station entrance (RSE) records** in user-supplied `490Stops.csv`. A single marker per station name uses the median of its mapped entrance coordinates. This is a London administrative-area export (area code 082), not a verified exhaustive list of every currently operational National Rail station within the exact Greater London polygon. The source includes some Elizabeth line stations; classifications may differ from ORR's station inventory. Station footprints are not included in this data. Station identifiers and source metadata are embedded in `station-data.js`.

Principal terminus markers use the agreed larger ring/dot style; other stations use the smaller ring.


## Consolidated Route Responsibility update (October 2026)

Adds five linked capabilities: archived Route polygon boundary display and ambiguity detection; coloured individual modelled railway links; station-to-Route spatial attribution; potential boundary/interface link highlighting; and ELR-to-Route geometric overlap search. These are **spatial inferences**, not authoritative current Route responsibility assignments. No operational asset-register, Sectional Appendix boundary verification, or current Network Rail responsibility data is included. Do not use for operational, safety-critical or legal responsibility decisions.

Method: project archived polygons and links into British National Grid (EPSG:27700); classify a link only if exactly one polygon covers >=98% of its length and all other polygons each overlap <2%. Other links remain unresolved; potential interface links have multiple or partial intersections. Classify NaPTAN station representative points only if exactly one polygon covers the point. ELR candidate Route lists derive from measured polygon intersection length and do not constitute verified ELR ownership. Boundary geometries are the original archived polygons, not a newly surveyed or legally precise boundary.

Files: `index.html`, `railway-data.js`, `station-data.js`, `responsibility-data.js`, `thames-osm-candidates.geojson`, `README.md`.
