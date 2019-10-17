---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394302"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>資料保護： DataProtection. AzureStorage 使用新的 Azure 儲存體 Api

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> 取決於[Azure 儲存體程式庫](https://github.com/Azure/azure-storage-net)。 這些程式庫會將其元件、封裝和命名空間重新命名。 從 ASP.NET Core 3.0 開始，`Microsoft.AspNetCore.DataProtection.AzureStorage` 會使用新的 `Microsoft.Azure.Storage.` 首碼的 Api 和套件。

如有 Azure 儲存體 Api 的相關問題，請使用 <https://github.com/Azure/azure-storage-net>。 如需此問題的討論，請參閱[aspnet/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

封裝參考了 `WindowsAzure.Storage` NuGet 套件。

#### <a name="new-behavior"></a>新的行為

此套件會參考 `Microsoft.Azure.Storage.Blob` NuGet 套件。

#### <a name="reason-for-change"></a>變更的原因

這種變更可讓 `Microsoft.AspNetCore.DataProtection.AzureStorage` 遷移至建議的 Azure 儲存體套件。

#### <a name="recommended-action"></a>建議的動作

如果您仍然需要使用具有 ASP.NET Core 3.0 的舊版 Azure 儲存體 Api，請新增[windowsazure.storage](https://www.nuget.org/packages/WindowsAzure.Storage/)套件的直接相依性。 此套件可以與新的 `Microsoft.Azure.Storage` Api 一起安裝。

在許多情況下，升級只牽涉到將 @no__t 0 的語句變更為使用新的命名空間：

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
