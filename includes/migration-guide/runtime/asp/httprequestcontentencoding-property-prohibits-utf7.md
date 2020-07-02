---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619817"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>HttpRequest.ContentEncoding 屬性禁止 UTF7

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，在 <xref:System.Web.HttpRequest?displayProperty=fullName> 本文中禁止使用 UTF-7 編碼。 在某些情況下，倚賴傳入 UTF-7 資料的應用程式資料將無法正確解碼。

#### <a name="suggestion"></a>建議

在理想情況下，您應該更新應用程式，不要在 <xref:System.Web.HttpRequest?displayProperty=fullName> 中使用 UTF-7 編碼。 或者，您也可以使用 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) 項目的 <code>aspnet:AllowUtf7RequestContentEncoding</code> 屬性還原舊版行為。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
