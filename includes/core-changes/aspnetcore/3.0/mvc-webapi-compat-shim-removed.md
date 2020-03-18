---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394403"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC：已刪除 Web API 相容性

從 ASP.NET 酷 3.0`Microsoft.AspNetCore.Mvc.WebApiCompatShim`開始，該包不再可用。

#### <a name="change-description"></a>變更描述

`Microsoft.AspNetCore.Mvc.WebApiCompatShim` （WebApiCompatShim） 包在ASP.NET酷中提供與ASP.NET 4.x Web API 2 的部分相容性，以簡化將現有 Web API 實現遷移到 ASP.NET Core。 但是，使用 WebApiCompatShim 的應用不會從最近ASP.NET核心版本中發佈的 API 相關功能中受益。 這些功能包括改進的 Open API 規範生成、標準化錯誤處理和用戶端代碼生成。 為了更好地集中 3.0 中的 API 工作，刪除了 WebApiCompatshim。 使用 WebApiCompatShim 的現有應用應遷移到較新的`[ApiController]`模型。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="reason-for-change"></a>更改原因

Web API 相容性是一個遷移工具。 它限制使用者訪問 ASP.NET Core 中添加的新功能。

#### <a name="recommended-action"></a>建議的動作

刪除此分片的使用，並直接遷移到ASP.NET核心本身的類似功能。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
