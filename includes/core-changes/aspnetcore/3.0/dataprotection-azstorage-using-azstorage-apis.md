---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440417"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a>資料保護： DataProtection 會使用新的 Azure 儲存體 Api

`Azure.Extensions.AspNetCore.DataProtection.Blobs` 相依于 [Azure 儲存體程式庫](https://github.com/Azure/azure-storage-net)。 這些程式庫會將其元件、封裝和命名空間重新命名。 從 ASP.NET Core 3.0 開始，會 `Azure.Extensions.AspNetCore.DataProtection.Blobs` 使用新 `Azure.Storage.` 首碼的 api 和套件。

如有 Azure 儲存體 Api 的相關問題，請使用 <https://github.com/Azure/azure-storage-net> 。 如需此問題的討論，請參閱 [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

封裝參考 `WindowsAzure.Storage` NuGet 套件。
套件會參考 `Microsoft.Azure.Storage.Blob` NuGet 套件。

#### <a name="new-behavior"></a>新的行為

套件會參考 `Azure.Storage.Blob` NuGet 套件。

#### <a name="reason-for-change"></a>變更的原因

這種變更可讓 `Azure.Extensions.AspNetCore.DataProtection.Blobs` 您遷移至建議的 Azure 儲存體套件。

#### <a name="recommended-action"></a>建議的動作

如果您仍然需要使用舊版 Azure 儲存體 Api 搭配 ASP.NET Core 3.0，請將直接相依性新增至 [WindowsAzure](https://www.nuget.org/packages/WindowsAzure.Storage/) 套件或 [Microsoft Azure 儲存體](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/)。 這個套件可以隨新的 api 一起安裝 `Azure.Storage` 。

在許多情況下，升級只牽涉到將 `using` 語句變更為使用新的命名空間：

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
