---
ms.openlocfilehash: 55a26f1ab27792cbedf3f31b797f37d3f768d51a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497248"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET 修正 WebForms CheckBox 控制項的 InputAttributes 和 LabelAttributes 處理方式

#### <a name="details"></a>詳細資料

若應用程式是以 .NET Framework 4.7.2 和更早版本為目標，回傳後會遺失以程式設計方式新增至 WebForms <xref:System.Web.UI.WebControls.CheckBox> 控制項的 <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> 和 <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType>。 若應用程式是以 .NET Framework 4.8 或更新版本為目標，則回傳後仍會保留這些項目。

#### <a name="suggestion"></a>建議

為了確保回傳時還原屬性的正確行為，請將 <code>targetFrameworkVersion</code> 設為 4.8 或更高。 例如：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>將它設得更低或完全不設時，則會保留既有的不正確行為。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |未知|
|版本|4.8|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.UI.WebControls.CheckBox`

-->
