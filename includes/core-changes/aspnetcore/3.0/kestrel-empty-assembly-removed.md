---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393932"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel： 空 HTTPS 程式集已刪除

程式集<xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName>已被刪除。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="reason-for-change"></a>更改原因

在 ASP.NET 核心 2.1`Microsoft.AspNetCore.Server.Kestrel.Https`中，的內容<xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>被移動到 。 此更改使用`[TypeForwardedTo]`屬性以非中斷的方式完成。

#### <a name="recommended-action"></a>建議的動作

- 引用 2.0 的`Microsoft.AspNetCore.Server.Kestrel.Https`庫應將所有ASP.NET核心依賴項更新為 2.1 或更高版本。 否則，它們可能會在載入到 ASP.NET 酷睿 3.0 應用中時中斷。
- 面向ASP.NET Core 2.1 和更高版本的應用和庫應刪除對`Microsoft.AspNetCore.Server.Kestrel.Https`NuGet 包的任何直接引用。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
