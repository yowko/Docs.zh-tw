---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291657"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure：已刪除 Microsoft 預固定的 Azure 集成包

提供ASP.NET`Microsoft.*`核心和 Azure SDK 之間集成的以下包不包括在 ASP.NET 酷 5.0 中：

* [微軟.擴展.配置.AzureKeyVault，](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/)它集成了[Azure 金鑰保存庫](/azure/key-vault/)到[配置系統](/aspnet/core/fundamentals/configuration/)。
* [微軟.AspNetCore.Data保護.AzureKeyVault，](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/)將Azure金鑰保存庫集成到[ASP.NET核心資料保護系統中](/aspnet/core/security/data-protection/introduction)。
* [微軟.AspNetCore.Data保護.Azure存儲](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)，將Azure [Blob存儲](/azure/storage/blobs/)集成到ASP.NET核心資料保護系統中。

有關此問題的討論，請參閱[dotnet/aspnetcore_19570](https://github.com/dotnet/aspnetcore/issues/19570)。

#### <a name="version-introduced"></a>介紹的版本

5.0 預覽 1

#### <a name="old-behavior"></a>舊的行為

這些`Microsoft.*`包將 Azure 服務與配置和資料保護 API 集成在一起。

#### <a name="new-behavior"></a>新的行為

新`Azure.*`包將 Azure 服務與配置和資料保護 API 集成。

#### <a name="reason-for-change"></a>更改原因

進行更改是因為`Microsoft.*`包是：

* 使用過時的 Azure SDK 版本。 無法進行簡單的更新，因為 Azure SDK 的新版本包含重大更改。
* 綁定到 .NET 核心發佈計畫。 將包的擁有權轉移到 Azure SDK 團隊可在 Azure SDK 更新時進行包更新。

#### <a name="recommended-action"></a>建議的動作

在ASP.NET Core 2.1 或更高版本的專案中`Microsoft.*`，用新`Azure.*`包替換舊包。

| 老 | 新增 |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure.AspNetCore.資料保護.金鑰](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure.AspNetCore.資料保護.Blob](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.擴展.配置.機密](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

新包使用 Azure SDK 的新版本，其中包括重大更改。 一般使用模式保持不變。 某些重載和選項可能不同，以適應基礎 Azure SDK API 中的更改。

舊包將：

* 在 .NET Core 2.1 和 3.1 的存留期內，由 ASP.NET 核心團隊提供支援。
* 不包括在 .NET 5 中。

將專案升級到 .NET 5 時，請`Azure.*`過渡到包以維護支援。

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
