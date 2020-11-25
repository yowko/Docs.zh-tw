---
title: 重大變更：延伸模組：套件參考變更會影響某些 NuGet 套件
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為延伸模組：影響某些 NuGet 套件的套件參考變更
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 4a525d9f7aad4409fd507fcf80c00968ff4b63d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760658"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a>擴充功能：套件參考變更會影響某些 NuGet 套件

藉由將某些 `Microsoft.Extensions.*` NuGet 套件從 [dotnet/extensions](https://github.com/dotnet/extensions) 存放庫遷移至 [dotnet/運行](https://github.com/dotnet/runtime)時間（如 [aspnet/公告 # 411](https://github.com/aspnet/Announcements/issues/411)所述），封裝變更會套用至某些已遷移的封裝。 如需此問題的討論，請參閱 [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 4

## <a name="old-behavior"></a>舊的行為

某些 `Microsoft.Extensions.*` 套件包含應用程式依賴之 api 的套件參考。

## <a name="new-behavior"></a>新的行為

您的應用程式可能必須新增套件相依性 `Microsoft.Extensions.*` 。

## <a name="reason-for-change"></a>變更的原因

封裝原則已更新，使其更符合 *dotnet/運行* 時間存放庫。 在新的原則下，未使用的封裝參考會在封裝期間從 *nupkg* 檔案中移除。

## <a name="recommended-action"></a>建議的動作

如果使用已移除套件相依性中的 Api，受影響套件的取用者應該在其專案中新增對已移除套件相依性的直接相依性。 下表列出受影響的封裝和對應的變更。

|套件名稱|變更描述|
|------------|------------------|
|[Microsoft.Extensions.Configuration。粘結 劑](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|已移除參考 `Microsoft.Extensions.Configuration`|
|[Microsoft.Extensions.Configuration.Js開啟](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |已移除參考 `System.Threading.Tasks.Extensions`|
|[。抽象概念](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|已移除參考 `Microsoft.Extensions.Logging.Abstractions`|
|[Microsoft.Extensions.Logging](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |已移除參考 `Microsoft.Extensions.Configuration.Binder`|
|[[登入] 主控台](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |已移除參考 `Microsoft.Extensions.Configuration.Abstractions`|
|[Microsoft 副檔名記錄檔。 EventLog](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |已移除 `System.Diagnostics.EventLog` .NET Framework 4.6.1 目標 Framework 標記的參考|
|[... 記錄檔 EventSource](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |已移除參考 `System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. 選項](https://nuget.org/packages/Microsoft.Extensions.Options)                          |已移除參考 `System.ComponentModel.Annotations`|

例如， `Microsoft.Extensions.Configuration` 已從移除的封裝參考 `Microsoft.Extensions.Configuration.Binder` 。 封裝中未使用相依性的 API。 相依于 `Microsoft.Extensions.Configuration.Binder` api 的使用者 `Microsoft.Extensions.Configuration` 應該在其專案中新增其直接參考。

## <a name="affected-apis"></a>受影響的 API

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
