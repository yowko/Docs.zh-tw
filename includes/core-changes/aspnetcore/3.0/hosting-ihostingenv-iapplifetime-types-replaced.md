---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394056"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>託管：IHosting 環境和 IApplicationLifetime 類型標記為過時並被替換

引入了新的類型來替換現有`IHostingEnvironment`類型和`IApplicationLifetime`類型。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`IHostingEnvironment`有兩種不同的`IApplicationLifetime`類型和類型從`Microsoft.Extensions.Hosting``Microsoft.AspNetCore.Hosting`和 。

#### <a name="new-behavior"></a>新的行為

舊類型已標記為過時，並替換為新類型。

#### <a name="reason-for-change"></a>更改原因

在`Microsoft.Extensions.Hosting`ASP.NET Core 2.1 中引入時`IHostingEnvironment`，`IApplicationLifetime`某些類型（`Microsoft.AspNetCore.Hosting`如 和）是從 中複製的。 某些ASP.NET Core 3.0 更改會導致應用同時`Microsoft.Extensions.Hosting`包含`Microsoft.AspNetCore.Hosting`和 命名空間。 引用兩個命名空間時，對這些重複類型的任何使用都會導致"模糊引用"編譯器錯誤。

#### <a name="recommended-action"></a>建議的動作

將舊類型的任何用法替換為新引入的類型，如下所示：

**過時類型（警告）：**

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

**新類型：**

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

新的`IHostEnvironment``IsDevelopment`和`IsProduction`擴充方法在`Microsoft.Extensions.Hosting`命名空間中。 可能需要將命名空間添加到專案中。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
