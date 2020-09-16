---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901705"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>資料保護： DataProtection. AzureStorage 使用新的 Azure 儲存體 Api

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> 相依于 [Azure 儲存體程式庫](https://github.com/Azure/azure-storage-net)。 這些程式庫會將其元件、封裝和命名空間重新命名。 從 ASP.NET Core 3.0 開始，會 `Microsoft.AspNetCore.DataProtection.AzureStorage` 使用新 `Microsoft.Azure.Storage.` 首碼的 api 和套件。

如有 Azure 儲存體 Api 的相關問題，請使用 <https://github.com/Azure/azure-storage-net> 。 如需此問題的討論，請參閱 [dotnet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

封裝參考 `WindowsAzure.Storage` NuGet 套件。

#### <a name="new-behavior"></a>新的行為

套件會參考 `Microsoft.Azure.Storage.Blob` NuGet 套件。

#### <a name="reason-for-change"></a>變更的原因

這種變更可讓 `Microsoft.AspNetCore.DataProtection.AzureStorage` 您遷移至建議的 Azure 儲存體套件。

#### <a name="recommended-action"></a>建議的動作

如果您仍然需要使用舊版 Azure 儲存體 Api 搭配 ASP.NET Core 3.0，請將直接相依性新增至 [WindowsAzure 的儲存體](https://www.nuget.org/packages/WindowsAzure.Storage/) 套件。 這個套件可以隨新的 api 一起安裝 `Microsoft.Azure.Storage` 。

在許多情況下，升級只牽涉到將 `using` 語句變更為使用新的命名空間：

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
