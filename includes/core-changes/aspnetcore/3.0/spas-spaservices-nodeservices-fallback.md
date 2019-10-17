---
ms.openlocfilehash: 1017801346e65940e4dc075ef72f7a00d7e6bcd9
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394132"
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

如果需要舊的行為，若要設定主控台記錄，請將 `services.AddLogging(builder => builder.AddConsole())` 新增至您的 @no__t 1 方法。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
