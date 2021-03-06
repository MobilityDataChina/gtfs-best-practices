---
path: /trips/
lang: en
---

### trips.txt

* __See special case for loop routes:__ Loop routes are cases where trips start and end at the same stop, as opposed to linear routes, which have two distinct termini. Loop routes must be described following specific practices. [See Loop route case.](/best-practices/#loop-routes)
* __See special case for lasso routes:__ Lasso routes are a hybrid of linear and loop geometries, in which vehicles travel on a loop for only a portion of the route. Lasso routes must be described following specific practices. [See Lasso route case.](/best-practices/#lasso-routes)

| Field Name | Recommendation |
| --- | --- |
| trip_headsign | Do not provide route names (matching `route_short_name` and `route_long_name`) in the `trip_headsign` or `stop_headsign` fields. |
| | Should contain destination, direction, and/or other trip designation text shown on the headsign of the vehicle which may be used to distinguish amongst trips in a route. Consistency with direction information shown on the vehicle is the primary and overriding goal for determining headsigns supplied in GTFS datasets. Other information should be included only if it does not compromise this primary goal. If headsigns change during a trip, override `trip_headsign` with `stop_times.stop_headsign`. Below are recommendations for some possible cases: |
| | example_table: <table class="example"><thead><tr><th>Route Description</th><th>Recommendation</th></tr></thead><tbody><tr><td>2A. Destination-only</td><td>Provide the terminus destination. e.g. "Transit Center", “Portland City Center”, or “Jantzen Beach”> </td></tr><tr><td>2B. Destinations with waypoints</td><td>&lt;destination&gt; via &lt;waypoint&gt; “Highgate via Charing Cross”. If waypoint(s) are removed from the headsign show to passengers after the vehicle passes those waypoints, use <code>stop_times.stop_headsign</code> to set an updated headsign.> </td></tr><tr><td>2C. Regional placename with local stops</td><td>If there will be multiple stops inside the city or borough of destination, use <code>stop_times.stop_headsign</code> once reaching the destination city.> </td></tr><tr><td>2D. Direction-only</td><td>Indicate using terms such as “Northbound”, “Inbound”, “Clockwise,” or similar directions.></td></tr><tr><td>2E. Direction with destination</td><td>&lt;direction&gt; to &lt;terminus name&gt; e.g. “Southbound to San Jose”></td></tr><tr><td>2F. Direction with destination and waypoints</td><td>&lt;direction&gt; via &lt;waypoint&gt; to &lt;destination&gt; (“Northbound via Charing Cross to Highgate”).></td></tr></tbody></table> |
| | Do not begin a headsign with the words “To” or “Towards”. |
| direction_id | If trips on a route service opposite directions, distinguish these groups of trips with the `direction_id` field, using values 0 and 1.|
| | Use values 0 and 1 consistently throughout the dataset. i.e.<ul><li>If 1 = Outbound on the Red route, then 1 = Outbound on the Green route</li><li>If 1 = Northbound on Route X, then 1 = Northbound on Route Y</li><li>If 1 = clockwise on Route X then 1 = clockwise on Route Y</li></ul> |
