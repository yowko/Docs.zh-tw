---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394097"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR： JavaScript 用戶端封裝名稱已變更

在 ASP.NET Core 3.0 Preview 7 中，SignalR JavaScript 用戶端封裝名稱從 `@aspnet/signalr` 變更為 `@microsoft/signalr`。 名稱變更反映出 SignalR 在不只是 ASP.NET Core 的應用程式中很有用的事實，因為 Azure SignalR Service。

若要回應這項變更，請變更您*封裝*中的參考、`require` 語句和 ECMAScript `import` 語句。 在此重新命名過程中，不會變更任何 API。

如需討論，請參閱[aspnet/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

用戶端套件的名稱為 `@aspnet/signalr`。

#### <a name="new-behavior"></a>新的行為

用戶端套件的名稱為 `@microsoft/signalr`。

#### <a name="reason-for-change"></a>變更的原因

[名稱] 變更清楚說明 SignalR 在 ASP.NET Core 應用程式之外很有用，因為 Azure SignalR Service。

#### <a name="recommended-action"></a>建議的動作

切換至新的封裝 `@microsoft/signalr`。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
