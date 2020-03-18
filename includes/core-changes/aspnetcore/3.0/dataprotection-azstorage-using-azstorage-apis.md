---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901705"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>資料保護：資料保護.Azure 存儲使用新的 Azure 存儲 API

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>取決於[Azure 存儲庫](https://github.com/Azure/azure-storage-net)。 這些庫重命名其程式集、包和命名空間。 從 ASP.NET 酷 3.0`Microsoft.AspNetCore.DataProtection.AzureStorage`開始`Microsoft.Azure.Storage.`，使用新的 -預定 API 和包。

有關 Azure 存儲 API 的問題，<https://github.com/Azure/azure-storage-net>請使用 。 有關此問題的討論，請參閱[dotnet/aspnetcore_8472](https://github.com/dotnet/aspnetcore/issues/8472)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

該包引用了`WindowsAzure.Storage`NuGet 包。

#### <a name="new-behavior"></a>新的行為

該包引用`Microsoft.Azure.Storage.Blob`NuGet 包。

#### <a name="reason-for-change"></a>更改原因

此更改允許`Microsoft.AspNetCore.DataProtection.AzureStorage`遷移到建議的 Azure 存儲包。

#### <a name="recommended-action"></a>建議的動作

如果仍需要將較舊的 Azure 存儲 API 與 ASP.NET Core 3.0 一起使用，則向[WindowsAzure.存儲](https://www.nuget.org/packages/WindowsAzure.Storage/)包添加直接依賴項。 此包可以與新`Microsoft.Azure.Storage`API 一起安裝。

在許多情況下，升級僅涉及更改`using`語句以使用新的命名空間：

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
