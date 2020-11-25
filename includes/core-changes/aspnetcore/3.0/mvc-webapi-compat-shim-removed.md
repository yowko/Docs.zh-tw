---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032397"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC：已移除 Web API 相容性填充碼

從 ASP.NET Core 3.0 開始， `Microsoft.AspNetCore.Mvc.WebApiCompatShim` 封裝已無法再使用。

#### <a name="change-description"></a>變更描述

`Microsoft.AspNetCore.Mvc.WebApiCompatShim` (的 >webapicompatshim) 套件提供 ASP.NET Core 中的部分相容性，以及 ASP.NET 4.X WEB api 2，以簡化將現有的 WEB api 部署遷移至 ASP.NET Core。 不過，使用 >webapicompatshim 的應用程式無法受益于最近 ASP.NET Core 版本中的 API 相關功能出貨。 這類功能包括改良的 Open API 規格產生、標準化錯誤處理和用戶端程式代碼產生。 為了更加專注于3.0 中的 API 工作，已移除 >webapicompatshim。 使用 >webapicompatshim 的現有應用程式應該遷移至較新的 `[ApiController]` 模型。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

Web API 相容性填充碼是一種遷移工具。 它會限制使用者存取 ASP.NET Core 中新增的功能。

#### <a name="recommended-action"></a>建議的動作

移除此填充碼的使用方式，並直接遷移至 ASP.NET Core 本身的類似功能。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
