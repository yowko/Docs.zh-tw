---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522674"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Spa： SpaServices 和 NodeServices 不會再切換回主控台記錄器

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType><xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType>除非已設定記錄，否則不會顯示主控台記錄。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`Microsoft.AspNetCore.SpaServices` 並且 `Microsoft.AspNetCore.NodeServices` 用來在未設定記錄時，自動建立主控台記錄器。

#### <a name="new-behavior"></a>新的行為

`Microsoft.AspNetCore.SpaServices``Microsoft.AspNetCore.NodeServices`除非已設定記錄，否則不會顯示主控台記錄。

#### <a name="reason-for-change"></a>變更的原因

您需要與其他 ASP.NET Core 封裝如何執行記錄。

#### <a name="recommended-action"></a>建議的動作

如果需要舊的行為，若要設定主控台記錄，請在您的方法中新增 `services.AddLogging(builder => builder.AddConsole())` `Setup.ConfigureServices` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!--

#### Affected APIs

Not detectable via API analysis

-->
