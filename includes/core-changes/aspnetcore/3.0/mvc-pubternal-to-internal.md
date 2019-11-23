---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394422"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC： "Pubternal" 類型已變更為內部

在 ASP.NET Core 3.0 中，MVC 中的所有 "pubternal" 類型都會更新為在支援的命名空間中 `public`，或視需要 `internal`。

#### <a name="change-description"></a>變更描述

在 ASP.NET Core 中，"pubternal" 類型會宣告為 `public`，但位於 `.Internal`尾碼命名空間中。 雖然這些類型是 `public`的，但它們沒有支援原則，而且可能會受到重大變更。 可惜的是，意外使用這些型別是很常見的，因而導致這些專案的重大變更，並限制維護架構的能力。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

MVC 中的某些類型已 `public`，但在 `.Internal` 命名空間中。 這些類型沒有支援原則，而且受限於中斷性變更。

#### <a name="new-behavior"></a>新的行為

所有這類類型都會更新為在支援的命名空間中 `public`，或標示為 `internal`。

#### <a name="reason-for-change"></a>變更的原因

意外使用 "pubternal" 類型是常見的，這會導致這些專案的重大變更，並限制維護架構的能力。

#### <a name="recommended-action"></a>建議的動作

如果您使用已確實 `public` 的類型，並已移至新的、支援的命名空間，請更新您的參考以符合新的命名空間。

如果您使用已標記為 `internal`的類型，您將需要尋找替代方案。 先前的 "pubternal" 類型絕不支援公開使用。 如果這些命名空間中有特定類型對您的應用程式很重要，請在[aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues)提出問題。 您可以考慮 `public`的要求類型。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

這項變更包含下列命名空間中的類型：

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
