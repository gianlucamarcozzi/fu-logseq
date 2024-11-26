## Next action
query-sort-by:: project
query-table:: true
query-sort-desc:: false
query-properties:: [:block :category :project]
{{query (property type next-action)}}
- ## Waiting for
  query-table:: true
  query-properties:: [:block :project]
  {{query (todo waiting)}}
- {{query (todo later)}}
  query-table:: true
  query-properties:: [:block :category :project]
- ## Someday maybe
  query-table:: true
  query-properties:: [:block :project]
	- {{query (property type someday-maybe)}}