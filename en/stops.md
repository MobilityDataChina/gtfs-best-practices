---
path: /stops/
lang: en
---

### stops.txt

| Field Name | Recommendation |
| --- | --- |
| stop_id | Stops that are in different physical locations (i.e., different designated precise locations for vehicles on designated routes to stop, potentially distinguished by signs, shelters, or other such public information, located on different street corners or representing different boarding facility such as a platform or bus bay, even if nearby each other) should have different `stop_id`.
| | `stop_id` is an internal ID, not intended to be shown to passengers. |
| | Maintain consistent `stop_id` for the same stops across data iterations (see [Dataset Publishing & General Practices](#dataset-publishing--general-practices)). |
| stop_name | The `stop_name` should match the agency's public name for the stop, station, or boarding facility, e.g. what is printed on a timetable, published online, and/or presented at the location.  |
| | When there is not a published stop name, follow consistent stop naming conventions throughout the feed.  |
| | Avoid use of abbreviations other than for places that are most commonly called by an abbreviated name. See Abbreviations (#2) under [All Files](#all-files).  |
| | Provide stop names in mixed case, following local conventions, as per recommendation for all customer-facing text fields.  |
| | By default, `stop_name` should not contain generic or redundant words like “Station” or “Stop”, but some edge cases are allowed.<ul><li>When it is actually part of the name (Union Station, Central Station<li>When the `stop_name` is too generic (such as if it is the name of the city). “Station”, “Terminal”, or other words make the meaning clear.</ul> |
| stop_lat & stop_lon | Stop locations should be as accurate possible. Stop locations should have an error of __no more__ than four meters when compared to the actual stop position. |
| | Stop locations should be placed very near to the pedestrian right of way where a passenger will board (i.e. correct side of the street). |
| | If a stop location is shared across separate data feeds (i.e. two agencies use exactly the same stop / boarding facility), indicate the stop is shared by using the exact same `stop_lat` and `stop_lon` for both stops. |
| stop_code | `stop_code` should be included in GTFS if there are passenger-facing stop numbers or short identifiers. |
| parent_station & location_type | Many stations or terminals have multiple boarding facilities (depending on mode, they might be called a bus bay, platform, wharf, gate, or another term). In such cases, feed producers should describe stations, boarding facilities (also called child stops), and their relation. <ul><li>The station or terminal should be defined as a record in `stops.txt` with `location_type = 1`.</li><li>Each boarding facility should be defined as a stop with `location_type = 0`. The `parent_station` field should reference the `stop_id` of the station the boarding facility is in.</li></ul> |
| | When naming the station and child stops, set names that are well-recognized by riders, and can help riders to identify the station and boarding facility (bus bay, platform, wharf, gate, etc.).<table class='example'><thead><tr><th>Parent Station Name</th><th>Child Stop Name</th></tr></thead><tbody><tr><td>Chicago Union Station</td><td>Chicago Union Station Platform 19</td></tr><tr><td>San Francisco Ferry Building Terminal</td><td>San Francisco Ferry Building Terminal Gate E</td></tr><tr><td>Downtown Transit Center</td><td>Downtown Transit Center Bay B</td></tr></tbody></table> |
