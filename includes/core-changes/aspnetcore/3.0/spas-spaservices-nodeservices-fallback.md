---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522674"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Spa： SpaServices 和 NodeServices 不再回到主控台記錄器

除非已設定記錄，否則 <xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> 和 <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> 不會顯示主控台記錄。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`Microsoft.AspNetCore.SpaServices` 和 `Microsoft.AspNetCore.NodeServices`，用於在未設定記錄時自動建立主控台記錄器。

#### <a name="new-behavior"></a>新的行為

除非已設定記錄，否則 `Microsoft.AspNetCore.SpaServices` 和 `Microsoft.AspNetCore.NodeServices` 不會顯示主控台記錄。

#### <a name="reason-for-change"></a>變更的原因

您必須配合其他 ASP.NET Core 封裝如何執行記錄。

#### <a name="recommended-action"></a>建議的動作

如果需要舊的行為，若要設定主控台記錄，請將 `services.AddLogging(builder => builder.AddConsole())` 新增至您的 `Setup.ConfigureServices` 方法。

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
