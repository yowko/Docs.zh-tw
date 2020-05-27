---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291657"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure：已移除 Microsoft 前面的 Azure 整合套件

`Microsoft.*`ASP.NET Core 5.0 中不包含下列提供 ASP.NET Core 與 Azure sdk 之間整合的套件：

* [AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/)，它會將[Azure Key Vault](/azure/key-vault/)整合至設定[系統](/aspnet/core/fundamentals/configuration/)。
* [AspNetCore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/)，可將 Azure Key Vault 整合到 ASP.NET Core 的[資料保護系統](/aspnet/core/security/data-protection/introduction)。
* [AspNetCore. DataProtection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)，可將[Azure Blob 儲存體](/azure/storage/blobs/)整合到 ASP.NET Core 的資料保護系統。

如需此問題的討論，請參閱[dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 1

#### <a name="old-behavior"></a>舊的行為

`Microsoft.*`套件整合了 Azure 服務與設定和資料保護 api。

#### <a name="new-behavior"></a>新的行為

新 `Azure.*` 的套件會整合 Azure 服務與設定和資料保護 api。

#### <a name="reason-for-change"></a>變更的原因

已進行變更，因為 `Microsoft.*` 封裝是：

* 使用過時版本的 Azure SDK。 不可能進行簡單的更新，因為新版本的 Azure SDK 包含重大變更。
* 系結至 .NET Core 發行排程。 將套件的擁有權轉移給 Azure SDK 小組會在更新 Azure SDK 時啟用套件更新。

#### <a name="recommended-action"></a>建議的動作

在 ASP.NET Core 2.1 或更新版本的專案中，以新的套件取代舊的 `Microsoft.*` `Azure.*` 。

| 多久 | 新增 |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [AspNetCore. DataProtection. 金鑰](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [AspNetCore. DataProtection Blob](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure 副檔名。秘密](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

新的套件會使用新版本的 Azure SDK，其中包含重大變更。 一般使用模式不會變更。 有些多載和選項可能會不同，以適應基礎 Azure SDK Api 中的變更。

舊的套件將會：

* 在 .NET Core 2.1 和3.1 的存留期間，由 ASP.NET Core 小組支援。
* 不包含在 .NET 5 中。

將您的專案升級至 .NET 5 時，請轉換至 `Azure.*` 套件以維持支援。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
