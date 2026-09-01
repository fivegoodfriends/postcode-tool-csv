🔓 **Important: This Repository Must Remain Public**

The postcode lookup step on the Webflow Welcome Forms depends on publicly accessible CSV data.

The postcode service list source of truth is stored in `raw_sharepoint_reference_data.postcode_tool_data`

**Do not change this repository to private.**

## Fetching source-of-truth data from Sisense

Use this query in Sisense to pull the current data mapped to this repo's CSV column names:

```sql
select
  postcode,
  acpr_code,
  acpr_name,
  region as state,
  strategy,
  zone as "Service Offering (26.09.2024)",
  null as "# FGF Members",
  null as "# BFHs (Employee Helpers) within 30km",
  bfh_welcome_visit,
  ndis_service_area as "NDIS Service Areas",
  f_2_f_signups as "F2F Signups",
  local_care_managment as "Local Care Management"
FROM postcode_tool_data
```

`# FGF Members` and `# BFHs (Employee Helpers) within 30km` are not tracked in
`postcode_tool_data` — they come back `null` and must be sourced separately.
