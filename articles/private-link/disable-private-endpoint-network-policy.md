---
title: Manage network policies for private endpoints
titleSuffix: Azure Private Link
description: Learn how to manage network policies for private endpoints.
services: private-link
author: asudbring
ms.service: private-link
ms.topic: how-to
ms.date: 07/26/2022
ms.author: allensu 
ms.custom: devx-track-azurepowershell, devx-track-azurecli 
ms.devlang: azurecli

---
# Manage network policies for private endpoints

By default, network policies are disabled for a subnet in a virtual network. To utilize network policies like UDR and NSG support, network policy support must be enabled for the subnet. This setting is only applicable to private endpoints within the subnet. This setting affects all private endpoints within the subnet. For other resources in the subnet, access is controlled based on security rules in the network security group.

> [!IMPORTANT]
> NSG and UDR support for private endpoints are in public preview on select regions. For more information, see [Public preview of Private Link UDR Support](https://azure.microsoft.com/updates/public-preview-of-private-link-udr-support/) and [Public preview of Private Link Network Security Group Support](https://azure.microsoft.com/updates/public-preview-of-private-link-network-security-group-support/).
> This preview version is provided without a service level agreement, and it's not recommended for production workloads. Certain features might not be supported or might have constrained capabilities. 
> For more information, see [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

You can use the following to enable or disable the setting:

* Azure portal

* Azure PowerShell

* Azure CLI

* Azure Resource Manager templates
 
The following examples describe how to enable and disable `PrivateEndpointNetworkPolicies` for a virtual network named **myVNet** with a **default** subnet of **10.1.0.0/24** hosted in a resource group named **myResourceGroup**.

## Enable network policy

# [**Portal**](#tab/network-policy-portal)

1. Sign-in to the [Azure portal](https://portal.azure.com).

2. In the search box at the top of the portal, enter **Virtual network**. Select **Virtual networks**.

3. Select **myVNet**.

4. In settings of **myVNet**, select **Subnets**.

5. Select the **default** subnet.

6. In the properties for the **default** subnet, select **Enabled** in **NETWORK POLICY FOR PRIVATE ENDPOINTS**.

7. Select **Save**.

# [**PowerShell**](#tab/network-policy-powershell)

Use [Get-AzVirtualNetwork](/powershell/module/az.network/get-azvirtualnetwork), [Set-AzVirtualNetworkSubnetConfig](/powershell/module/az.network/set-azvirtualnetworksubnetconfig), and [Set-AzVirtualNetwork](/powershell/module/az.network/set-azvirtualnetwork) to enable the policy.

```azurepowershell
$net = @{
    Name = 'myVNet'
    ResourceGroupName = 'myResourceGroup'
}
$vnet = Get-AzVirtualNetwork @net

$sub = @{
    Name = 'default'
    VirtualNetwork = $vnet
    AddressPrefix = '10.1.0.0/24'
    PrivateEndpointNetworkPoliciesFlag = 'Enabled'
}
Set-AzVirtualNetworkSubnetConfig @sub

$vnet | Set-AzVirtualNetwork
```

# [**CLI**](#tab/network-policy-cli)

Use [az network vnet subnet update](/cli/azure/network/vnet/subnet#az-network-vnet-subnet-update) to enable the policy.

```azurecli
az network vnet subnet update \
  --disable-private-endpoint-network-policies false \
  --name default \
  --resource-group myResourceGroup \
  --vnet-name myVNet
```

# [**JSON**](#tab/network-policy-json)

This section describes how to enable subnet private endpoint policies using an Azure Resource Manager template.

```json
{ 
          "name": "myVNet", 
          "type": "Microsoft.Network/virtualNetworks", 
          "apiVersion": "2019-04-01", 
          "location": "WestUS", 
          "properties": { 
                "addressSpace": { 
                     "addressPrefixes": [ 
                          "10.1.0.0/16" 
                        ] 
                  }, 
                  "subnets": [ 
                         { 
                                "name": "default", 
                                "properties": { 
                                    "addressPrefix": "10.1.0.0/24", 
                                    "privateEndpointNetworkPolicies": "Enabled" 
                                 } 
                         } 
                  ] 
          } 
} 
```

---

## Disable network policy

# [**Portal**](#tab/network-policy-portal)

1. Sign-in to the [Azure portal](https://portal.azure.com).

2. In the search box at the top of the portal, enter **Virtual network**. Select **Virtual networks**.

3. Select **myVNet**.

4. In settings of **myVNet**, select **Subnets**.

5. Select the **default** subnet.

6. In the properties for the **default** subnet, select **Disabled** in **NETWORK POLICY FOR PRIVATE ENDPOINTS**.

7. Select **Save**.

# [**PowerShell**](#tab/network-policy-powershell)

Use [Get-AzVirtualNetwork](/powershell/module/az.network/get-azvirtualnetwork), [Set-AzVirtualNetwork](/powershell/module/az.network/set-azvirtualnetwork), and [Set-AzVirtualNetworkSubnetConfig](/powershell/module/az.network/set-azvirtualnetworksubnetconfig) to disable the policy.

```azurepowershell
$net = @{
    Name = 'myVNet'
    ResourceGroupName = 'myResourceGroup'
}
$vnet = Get-AzVirtualNetwork @net

$sub = @{
    Name = 'default'
    VirtualNetwork = $vnet
    AddressPrefix = '10.1.0.0/24'
    PrivateEndpointNetworkPoliciesFlag = 'Disabled'
}
Set-AzVirtualNetworkSubnetConfig @sub

$vnet | Set-AzVirtualNetwork
```

# [**CLI**](#tab/network-policy-cli)

Use [az network vnet subnet update](/cli/azure/network/vnet/subnet#az-network-vnet-subnet-update) to disable the policy.

```azurecli
az network vnet subnet update \
  --disable-private-endpoint-network-policies true \
  --name default \
  --resource-group myResourceGroup \
  --vnet-name myVNet
  
```

# [**JSON**](#tab/network-policy-json)

This section describes how to disable subnet private endpoint policies using an Azure Resource Manager template.

```json
{ 
          "name": "myVNet", 
          "type": "Microsoft.Network/virtualNetworks", 
          "apiVersion": "2019-04-01", 
          "location": "WestUS", 
          "properties": { 
                "addressSpace": { 
                     "addressPrefixes": [ 
                          "10.1.0.0/16" 
                        ] 
                  }, 
                  "subnets": [ 
                         { 
                                "name": "default", 
                                "properties": { 
                                    "addressPrefix": "10.1.0.0/24", 
                                    "privateEndpointNetworkPolicies": "Disabled" 
                                 } 
                         } 
                  ] 
          } 
} 
```

---

## Next steps
- Learn more about [Azure private endpoint](private-endpoint-overview.md)
 
