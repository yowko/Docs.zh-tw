---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393932"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel：已移除空的 HTTPS 元件

元件 <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> 已移除。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

在 ASP.NET Core 2.1 中，`Microsoft.AspNetCore.Server.Kestrel.Https` 的內容已移至 <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>。 這項變更是使用 `[TypeForwardedTo]` 屬性，以不間斷的方式完成。

#### <a name="recommended-action"></a>建議的動作

- 參考 `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 的程式庫應該將所有 ASP.NET Core 相依性更新為2.1 或更新版本。 否則，它們可能會在載入 ASP.NET Core 3.0 應用程式時中斷。
- 以 ASP.NET Core 2.1 和更新版本為目標的應用程式和程式庫，應移除任何 `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet 套件的直接參考。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
