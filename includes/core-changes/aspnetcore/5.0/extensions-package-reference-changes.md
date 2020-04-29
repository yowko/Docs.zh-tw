---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507069"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a>延伸模組：套件參考變更會影響某些 NuGet 套件

`Microsoft.Extensions.*`透過將[dotnet/extensions](https://github.com/dotnet/extensions)存放庫中的某些 NuGet 套件遷移至[dotnet/Runtime](https://github.com/dotnet/runtime)（如[aspnet/公告 # 411](https://github.com/aspnet/Announcements/issues/411)所述），封裝變更會套用至某些已遷移的封裝。 如需此問題的討論，請參閱[dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 4

#### <a name="old-behavior"></a>舊的行為

某些`Microsoft.Extensions.*`套件包含應用程式所依賴之 api 的套件參考。

#### <a name="new-behavior"></a>新的行為

您的應用程式可能必須`Microsoft.Extensions.*`新增套件相依性。

#### <a name="reason-for-change"></a>變更的原因

已更新封裝原則，使其更符合*dotnet/runtime*存放庫。 在新原則下，封裝期間會從*nupkg*檔案中移除未使用的套件參考。

#### <a name="recommended-action"></a>建議的動作

如果使用來自已移除封裝相依性的 Api，受影響套件的取用者應該在其專案中加入已移除封裝相依性的直接相依性。 下表列出受影響的封裝和對應的變更。

|套件名稱|變更描述|
|------------|------------------|
|[設定系結器](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|已移除的參考`Microsoft.Extensions.Configuration`|
|[設定 Json](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |已移除的參考`System.Threading.Tasks.Extensions`|
|[Microsoft Extensions. 主控抽象概念](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|已移除的參考`Microsoft.Extensions.Logging.Abstractions`|
|[Microsoft.Extensions.Logging](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |已移除的參考`Microsoft.Extensions.Configuration.Binder`|
|[[Microsoft Extensions] 主控台](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |已移除的參考`Microsoft.Extensions.Configuration.Abstractions`|
|[Microsoft Extensions. EventLog](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |已移除 .NET Framework `System.Diagnostics.EventLog` 4.6.1 目標 Framework 標記的參考|
|[Microsoft Extensions. 記錄檔 EventSource](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |已移除的參考`System.Threading.Tasks.Extensions`|
|[Microsoft Extensions 選項](https://nuget.org/packages/Microsoft.Extensions.Options)                          |已移除的參考`System.ComponentModel.Annotations`|

例如，的封裝參考`Microsoft.Extensions.Configuration`已從中`Microsoft.Extensions.Configuration.Binder`移除。 套件中未使用相依性的 API。 `Microsoft.Extensions.Configuration.Binder`相依于的 api 的使用者`Microsoft.Extensions.Configuration`應該在其專案中新增其直接參考。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!--

#### Affected APIs

Not detectable via API analysis

-->
