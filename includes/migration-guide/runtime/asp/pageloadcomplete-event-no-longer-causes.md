---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619929"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Page.LoadComplete 事件不再導致 System.Web.UI.WebControls.EntityDataSource 控制項叫用資料繫結

#### <a name="details"></a>詳細資料

<xref:System.Web.UI.Page.LoadComplete> 事件不再使 <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> 控制項叫用資料繫結，讓變更建立/更新/刪除參數。 這項變更可以消除來回存取資料庫的額外作業，防止重設控制項的值，並且產生與其他資料控制項 (例如 <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> 和 <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>) 一致的行為。 在像是應用程式倚賴於 <xref:System.Web.UI.Page.LoadComplete> 事件中叫用資料繫結這類不常見的情況下，這項變更會產生不同的行為。

#### <a name="suggestion"></a>建議

如果需要資料繫結，請在回傳初期的事件中手動叫用資料繫結。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段|
