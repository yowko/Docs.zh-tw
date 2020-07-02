---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615618"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter 無法正確轉譯 `<br/>` 項目

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6 開始，使用 `<BR />` 項目呼叫 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> 和 <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> 將會正確地只插入一個 `<BR />` (而不是兩個)

#### <a name="suggestion"></a>建議

如果應用程式需要額外的 `<BR />` 標籤，則應該再次呼叫 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)>。 請注意，這項行為變更只會影響以 .NET Framework 4.6 或更新版本為目標的應用程式，因此另一個做法是以舊版 .NET Framework 為目標，以取得舊版行為。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
