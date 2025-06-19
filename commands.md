Services: 
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/services" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_services.json
```

Routes
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/routes" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_routes.json
```

Plugins
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/plugins" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_plugins.json
```

Consumers 
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/consumers" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_consumers.json
```

Upstreams
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/upstreams" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_upstreams.json
```

Targets 
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/targets" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_targets.json
```

Certificates
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/certificates" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_certificates.json
```

snis
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/snis" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_snis.json
```

vaults 
```
curl -s -X GET \
  "https://us.api.konghq.com/v2/control-planes/0b9976f8-db71-4c27-80fe-e9e411d94f24/core-entities/vaults" \
  --header "Authorization: Bearer kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" | jq > kong_vaults.json
```

Full export using deck 
```
deck gateway dump \
  --konnect-control-plane-name="zinnia_dev" \
  --konnect-token="kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" \
  --workspace default \
  --output-file full-export.yaml
```

Plan - 
```
zinnia_india@Sonawane-Vidya-J3JH65KJQ1 zinnia_dev_cloud % deck gateway diff \
  --konnect-control-plane-name="Zinnia Dev Cloud" \
  --konnect-token="kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" \
  zinnia_dev_cloud.yaml
creating service ciam-audit_zinnia_dev
creating route CIAM_Audit_Service-searchAuditLogs
creating route CIAM_Audit_Service-createAuditLog
creating plugin file-log for service ciam-audit_zinnia_dev
creating plugin opentelemetry for service ciam-audit_zinnia_dev
creating plugin openid-connect for route CIAM_Audit_Service-searchAuditLogs
creating plugin openid-connect for route CIAM_Audit_Service-createAuditLog
Summary:
  Created: 7
  Updated: 0
  Deleted: 0
```

Apply - 
```
zinnia_india@Sonawane-Vidya-J3JH65KJQ1 zinnia_dev_cloud % deck gateway sync \
  --konnect-control-plane-name="Zinnia Dev Cloud" \
  --konnect-token="kpat_JHcpixfkm5EYQ8ri4UNcdHUMyeseblywSHDVGxuQYqsgKW2a0" \
  zinnia_dev_cloud.yaml
creating service ciam-audit_zinnia_dev
creating route CIAM_Audit_Service-createAuditLog
creating route CIAM_Audit_Service-searchAuditLogs
creating plugin file-log for service ciam-audit_zinnia_dev
creating plugin openid-connect for route CIAM_Audit_Service-createAuditLog
creating plugin opentelemetry for service ciam-audit_zinnia_dev
creating plugin openid-connect for route CIAM_Audit_Service-searchAuditLogs
Summary:
  Created: 6
  Updated: 0
  Deleted: 0
Error: 1 errors occurred:
	while processing event: Create plugin file-log for service ciam-audit_zinnia_dev failed: HTTP status 400 (message: "validation error: plugin(file-log) does not exist")
```