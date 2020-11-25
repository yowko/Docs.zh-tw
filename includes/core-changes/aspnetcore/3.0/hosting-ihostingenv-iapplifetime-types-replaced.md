---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032353"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>裝載：標示為已淘汰和已取代的 IHostingEnvironment 和 IApplicationLifetime 類型

引進了新的類型來取代現有 `IHostingEnvironment` 的和 `IApplicationLifetime` 類型。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

和中有兩種不同的 `IHostingEnvironment` 和 `IApplicationLifetime` 類型 `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting` 。

#### <a name="new-behavior"></a>新的行為

舊型別已標示為已淘汰，並取代為新的類型。

#### <a name="reason-for-change"></a>變更的原因

當 `Microsoft.Extensions.Hosting` ASP.NET Core 2.1 引進時，會從複製一些類型，例如 `IHostingEnvironment` 和 `IApplicationLifetime` `Microsoft.AspNetCore.Hosting` 。 部分 ASP.NET Core 3.0 變更會導致應用程式同時包含 `Microsoft.Extensions.Hosting` 和 `Microsoft.AspNetCore.Hosting` 命名空間。 當參考兩個命名空間時，使用這些重複的類型會導致「不明確參考」編譯器錯誤。

#### <a name="recommended-action"></a>建議的動作

以新引進的類型取代舊型別的任何使用方式，如下所示：

**過時的類型 (警告) ：**

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

新的 `IHostEnvironment` `IsDevelopment` 和 `IsProduction` 擴充方法位於 `Microsoft.Extensions.Hosting` 命名空間中。 可能需要將該命名空間新增至您的專案。

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
