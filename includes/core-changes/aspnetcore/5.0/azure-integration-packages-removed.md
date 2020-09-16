---
ms.openlocfilehash: 19ccdb634d4e53ea66c032502f2adb70423ab121
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416260"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure：已移除的 Microsoft 首碼 Azure 整合套件

下列 `Microsoft.*` 封裝可提供 ASP.NET Core 和 Azure sdk 之間的整合，但不包含在 ASP.NET Core 5.0 中：

* [Microsoft.Extensions.Configuration。AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/)，會將 [Azure Key Vault](/azure/key-vault/) 整合至設定 [系統](/aspnet/core/fundamentals/configuration/)。
* [AspNetCore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/)，可將 Azure Key Vault 整合到 [ASP.NET Core 資料保護系統](/aspnet/core/security/data-protection/introduction)中。
* [AspNetCore. DataProtection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)，可將 [Azure Blob 儲存體](/azure/storage/blobs/) 整合到 ASP.NET Core 資料保護系統中。

如需此問題的討論，請參閱 [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 1

#### <a name="old-behavior"></a>舊的行為

`Microsoft.*`套件整合了 Azure 服務與設定和資料保護 api。

#### <a name="new-behavior"></a>新的行為

新 `Azure.*` 套件會整合 Azure 服務與設定和資料保護 api。

#### <a name="reason-for-change"></a>變更的原因

變更的原因是因為 `Microsoft.*` 封裝：

* 使用過期版本的 Azure SDK。 因為新版本的 Azure SDK 包含了重大變更，所以不可能進行簡單的更新。
* 與 .NET Core 發行排程相關聯。 將套件的擁有權轉移給 Azure SDK 小組可在 Azure SDK 更新時啟用套件更新。

#### <a name="recommended-action"></a>建議的動作

在 ASP.NET Core 2.1 或更新版本的專案中，將舊的取代為 `Microsoft.*` 新的 `Azure.*` 套件。

| 老 | 新增 |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [AspNetCore. DataProtection 金鑰](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [AspNetCore. DataProtection Blob](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.AspNetCore.Configuration。秘密](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

新的套件會使用新版本的 Azure SDK，其中包含重大變更。 一般使用模式不會變更。 某些多載和選項可能不同，以適應基礎 Azure SDK Api 中的變更。

舊的封裝將會：

* 在 .NET Core 2.1 和3.1 的存留期內，ASP.NET Core 團隊支援。
* 不包含在 .NET 5 中。

將專案升級至 .NET 5 時，請轉換至 `Azure.*` 封裝以維持支援。

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
