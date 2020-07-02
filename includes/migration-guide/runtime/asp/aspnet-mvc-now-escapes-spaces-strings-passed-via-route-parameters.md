---
ms.openlocfilehash: c53fe57f3278741a927a2f00b11af6e26dafce66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619928"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC 現在會將透過路由參數傳入之字串中的空格逸出

#### <a name="details"></a>詳細資料

為了遵守 RFC 2396，從路由填入動作參數時，現在會將路由路徑中的空格逸出。 因此，雖然 <code>/controller/action/some data</code> 先前會比對路由 <code>/controller/action/{data}</code> 並提供 <code>some data</code> 作為資料參數，但現在會改為提供 <code>some%20data</code>。

#### <a name="suggestion"></a>建議

您應該更新程式碼，以將路由中的字串參數設為未逸出。 如果需要原始 URI，您可以使用 <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API 來存取。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5.2|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
