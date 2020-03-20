---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803177"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC 現在會將透過路由參數傳入之字串中的空格逸出

|   |   |
|---|---|
|詳細資料|為了遵守 RFC 2396，從路由填入動作參數時，現在會將路由路徑中的空格逸出。 因此，雖然 <code>/controller/action/some data</code> 先前會比對路由 <code>/controller/action/{data}</code> 並提供 <code>some data</code> 作為資料參數，但現在會改為提供 <code>some%20data</code>。|
|建議|您應該更新程式碼，以將路由中的字串參數設為未逸出。 如果需要原始 URI，您可以使用 <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API 來存取。|
|影響範圍|Minor|
|版本|4.5.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
