---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032349"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>裝載：泛型主機限制啟動的函式插入

泛型主機針對類別的函式插入所支援的唯一類型為 `Startup` `IHostEnvironment` 、 `IWebHostEnvironment` 和 `IConfiguration` 。 使用的應用程式 `WebHost` 不會受到影響。

#### <a name="change-description"></a>變更描述

在 ASP.NET Core 3.0 之前，您可以在類別的函式中，將函式插入用於任意類型 `Startup` 。 在 ASP.NET Core 3.0 中，web 堆疊已 replatformed 至一般主機程式庫。 您可以在範本的 *Program.cs* 檔案中看到變更：

**ASP.NET Core 2.x：**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3.0：**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` 使用一個相依性插入 (DI) 容器來建立應用程式。 `WebHost` 使用兩個容器：一個用於主機，另一個用於應用程式。 因此，此函式 `Startup` 不再支援自訂服務插入。 只有 `IHostEnvironment` 、 `IWebHostEnvironment` 和 `IConfiguration` 可以插入。 這項變更可防止 DI 問題（例如重複建立單一服務）。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

這項變更是將 web 堆疊遷移至一般主機程式庫的結果。

#### <a name="recommended-action"></a>建議的動作

將服務插入方法簽章中 `Startup.Configure` 。 例如：

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
