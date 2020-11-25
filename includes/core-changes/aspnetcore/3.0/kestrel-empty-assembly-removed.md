---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032381"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel：已移除空白的 HTTPS 元件

元件 <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> 已被移除。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

在 ASP.NET Core 2.1 中，的內容 `Microsoft.AspNetCore.Server.Kestrel.Https` 已移至 <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> 。 這項變更是以使用屬性的非中斷方式進行 `[TypeForwardedTo]` 。

#### <a name="recommended-action"></a>建議的動作

- 參考2.0 的程式庫 `Microsoft.AspNetCore.Server.Kestrel.Https` 應該將所有 ASP.NET Core 相依性更新至2.1 或更新版本。 否則，它們可能會在載入至 ASP.NET Core 3.0 應用程式時中斷。
- 以 ASP.NET Core 2.1 和更新版本為目標的應用程式和程式庫應移除 NuGet 套件的任何直接參考 `Microsoft.AspNetCore.Server.Kestrel.Https` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
