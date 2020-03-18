---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901762"
---
### <a name="signalr-javascript-client-package-name-changed"></a>信號R：JavaScript用戶端包名稱已更改

在ASP.NET酷3.0預覽7中，SignalR JavaScript用戶端包名稱從`@aspnet/signalr`更改為`@microsoft/signalr`。 名稱更改反映了一個事實，即由於 Azure SignalR 服務，SignalR 不僅在 ASP.NET 核心應用中非常有用。

要對此更改做出反應，請更改*包.json*檔、`require`語句和 ECMAScript`import`語句中的引用。 作為此重命名的一部分，任何 API 都不會改變。

有關討論，請參閱[點網/阿斯平核心#11637](https://github.com/dotnet/aspnetcore/issues/11637)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

用戶端包已命名`@aspnet/signalr`。

#### <a name="new-behavior"></a>新的行為

用戶端包名為`@microsoft/signalr`。

#### <a name="reason-for-change"></a>更改原因

名稱更改闡明，由於 Azure SignalR 服務，SignalR 在 ASP.NET 核心應用之外非常有用。

#### <a name="recommended-action"></a>建議的動作

切換到新包`@microsoft/signalr`。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
