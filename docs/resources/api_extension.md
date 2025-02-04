---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "commercetools_api_extension Resource - terraform-provider-commercetools"
subcategory: ""
description: |-
  Create a new API extension to extend the bevahiour of an API with business logic. Note that API extensions affect the performance of the API it is extending. If it fails, the whole API call fails
  Also see the API Extension API Documentation https://docs.commercetools.com/api/projects/api-extensions
---

# commercetools_api_extension (Resource)

Create a new API extension to extend the bevahiour of an API with business logic. Note that API extensions affect the performance of the API it is extending. If it fails, the whole API call fails 

Also see the [API Extension API Documentation](https://docs.commercetools.com/api/projects/api-extensions)

## Example Usage

```terraform
resource "commercetools_api_extension" "my-extension" {
  key = "my-extension-key"

  destination {
    type                 = "HTTP"
    url                  = "https://example.com"
    authorization_header = "Basic 12345"
  }

  trigger {
    resource_type_id = "customer"
    actions          = ["Create", "Update"]
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `destination` (Block List, Min: 1, Max: 1) [Destination](https://docs.commercetools.com/api/projects/api-extensions#destination) Details where the extension can be reached (see [below for nested schema](#nestedblock--destination))
- `trigger` (Block List, Min: 1) Array of [Trigger](https://docs.commercetools.com/api/projects/api-extensions#trigger) Describes what triggers the extension (see [below for nested schema](#nestedblock--trigger))

### Optional

- `key` (String) User-specific unique identifier for the extension
- `timeout_in_ms` (Number) Extension timeout in milliseconds

### Read-Only

- `id` (String) The ID of this resource.
- `version` (Number)

<a id="nestedblock--destination"></a>
### Nested Schema for `destination`

Required:

- `type` (String)

Optional:

- `access_key` (String)
- `access_secret` (String, Sensitive)
- `arn` (String)
- `authorization_header` (String)
- `azure_authentication` (String)
- `url` (String)


<a id="nestedblock--trigger"></a>
### Nested Schema for `trigger`

Required:

- `actions` (List of String) Currently, Create and Update are supported
- `resource_type_id` (String) Currently, cart, order, payment, and customer are supported

Optional:

- `condition` (String) Valid predicate that controls the conditions under which the API Extension is called.
