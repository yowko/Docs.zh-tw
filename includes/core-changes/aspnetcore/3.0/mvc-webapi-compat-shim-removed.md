---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394403"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC： Web API 相容性填充碼已移除

從 ASP.NET Core 3.0 開始，`Microsoft.AspNetCore.Mvc.WebApiCompatShim` 封裝已無法再使用。

#### <a name="change-description"></a>變更描述

@No__t-0 （WebApiCompatShim）套件提供 ASP.NET 4.x Web API 2 ASP.NET Core 的部分相容性，以簡化將現有的 Web API 部署遷移至 ASP.NET Core 的工作。 不過，使用 WebApiCompatShim 的應用程式不會受益于最近 ASP.NET Core 版本中的 API 相關功能隨附。 這類功能包括改良的開放式 API 規格產生、標準化的錯誤處理，以及用戶端程式代碼產生。 為了更專注于3.0 中的 API 工作，已移除 WebApiCompatShim。 使用 WebApiCompatShim 的現有應用程式應該遷移至較新的 `[ApiController]` 模型。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

Web API 相容性填充碼是一種遷移工具。 它會限制使用者存取 ASP.NET Core 中新增的功能。

#### <a name="recommended-action"></a>建議的動作

移除此填充碼的使用方式，並直接遷移至 ASP.NET Core 本身的類似功能。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
