# terraform-azure Public IP module
Public IP addresses allow Internet resources to communicate inbound to Azure resources. Public IP addresses enable Azure resources to communicate to Internet and public-facing Azure services. This module allows you to create multiple static Public IP's with a set of public ip names. By default the SKU of the Public IP resource is Basic. In this module we changed that to Standard, since we most likely will use these IP's for the ingress controller which requires Standard SKU.

## Usage

```hcl
module "public-ip" {
  source              = "guidalabs/terraform-azure-public-ip"
  resource_group_name = azurerm_resource_group.main.name
  location            = local.location
  public_ips          = toset(["ingress1", "ingress2"])
  sku                 = "Standard"
}
```