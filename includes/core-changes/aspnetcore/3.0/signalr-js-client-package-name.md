---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032424"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR： JavaScript 用戶端套件名稱已變更

在 ASP.NET Core 3.0 Preview 7 中，SignalR JavaScript 用戶端套件名稱已從變更 `@aspnet/signalr` 為 `@microsoft/signalr` 。 名稱變更反映了 Azure SignalR Service，而不只是 ASP.NET Core 的應用程式，SignalR 會很有用。

若要回應這項變更，請在檔案 *package.json* 、 `require` 語句和 ECMAScript 語句上變更package.js中的參考 `import` 。 此重新命名過程中不會變更任何 API。

如需討論，請參閱 [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

用戶端封裝的名稱為 `@aspnet/signalr` 。

#### <a name="new-behavior"></a>新的行為

用戶端封裝的名稱為 `@microsoft/signalr` 。

#### <a name="reason-for-change"></a>變更的原因

名稱變更指出，SignalR 在 Azure SignalR Service 的情況下，對 ASP.NET Core 應用程式來說很有用。

#### <a name="recommended-action"></a>建議的動作

切換至新的封裝 `@microsoft/signalr` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
