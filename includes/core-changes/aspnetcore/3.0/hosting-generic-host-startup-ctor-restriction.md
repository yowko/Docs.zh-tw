---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901820"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>託管：通用主機限制啟動建構函式注入

類建構函式注入的泛型主機`Startup`支援的唯一類型是`IHostEnvironment``IWebHostEnvironment`和`IConfiguration`。 使用`WebHost`的應用不受影響。

#### <a name="change-description"></a>變更描述

在ASP.NET Core 3.0 之前，建構函式注入可用於類建構函式中的`Startup`任意類型。 在 ASP.NET Core 3.0 中，Web 堆疊重新平臺化到通用主機庫。 您可以在範本的*Program.cs*檔中看到更改：

**ASP.NET核心 2.x：**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET核心 3.0：**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`使用一個依賴項注入 （DI） 容器來生成應用。 `WebHost`使用兩個容器：一個用於主機，一個用於應用。 因此，`Startup`建構函式不再支援自訂服務注入。 只能`IHostEnvironment`注入`IWebHostEnvironment`，`IConfiguration`並且可以注入。 此更改可防止 DI 問題，例如重複創建單例服務。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="reason-for-change"></a>更改原因

此更改是將 Web 堆疊重新平臺到通用主機庫的結果。

#### <a name="recommended-action"></a>建議的動作

將服務注入`Startup.Configure`方法簽名。 例如：

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
