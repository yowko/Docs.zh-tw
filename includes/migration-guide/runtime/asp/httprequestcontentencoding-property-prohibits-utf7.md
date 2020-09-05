---
ms.openlocfilehash: cf34c5df1badcfd86d8a07bafdf1b759234712e0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497165"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>HttpRequest.ContentEncoding 屬性禁止 UTF7

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，在 <xref:System.Web.HttpRequest?displayProperty=fullName> 本文中禁止使用 UTF-7 編碼。 在某些情況下，倚賴傳入 UTF-7 資料的應用程式資料將無法正確解碼。

#### <a name="suggestion"></a>建議

在理想情況下，您應該更新應用程式，不要在 <xref:System.Web.HttpRequest?displayProperty=fullName> 中使用 UTF-7 編碼。 或者，您也可以使用 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) 項目的 <code>aspnet:AllowUtf7RequestContentEncoding</code> 屬性還原舊版行為。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.ContentEncoding`

-->
