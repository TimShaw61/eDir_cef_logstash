# eDir_cef_logstash
Logstash rules for parsing eDirectory audit logging in CEF format

XDAS audit logging of eDirectory events is deprecated in OES 2018SP2 with eDirectory 9.2
The new CEF format was adopted because Microfocus bought ArcSight who created the format.

It was always awkward to parse the output from eDirectory XDAS instrumentation because the JSON produced was nested and needed to be 'flattened' before processing by logstash. Spaces in the JSON Keys had to be dealt with and there was no convenient short message field to summarise the event.

All this is improved in the CEF format but there is still some tricky parsing of the event data required which this logstash configuration file attempts to solve.

Suggestions for improvement welcome

logstash does not have the gelf output plugin by default so it will need to be installed:

<code>bin/logstash-plugin install logstash-output-gelf</code>

To use the date formatter to alter date formats from m/d/y to d/m/y you will need the date_formatter plugin too:

<code>bin/logstash-plugin install logstash-filter-date_formatter</code>
