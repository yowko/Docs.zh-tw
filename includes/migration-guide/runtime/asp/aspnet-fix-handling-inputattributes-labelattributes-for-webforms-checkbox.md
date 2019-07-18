---
ms.openlocfilehash: e605e0f2636d83745815ec4ed27bf72692f18d15
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802639"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET 修正 WebForms CheckBox 控制項的 InputAttributes 和 LabelAttributes 處理方式

|   |   |
|---|---|
|詳細資料|若應用程式是以 .NET Framework 4.7.2 和更早版本為目標，回傳後會遺失以程式設計方式新增至 WebForms <xref:System.Web.UI.WebControls.CheckBox> 控制項的 <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> 和 <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType>。 若應用程式是以 .NET Framework 4.8 或更新版本為目標，則回傳後仍會保留這些項目。|
|建議|為了確保回傳時還原屬性的正確行為，請將 <code>targetFrameworkVersion</code> 設為 4.8 或更高。 例如：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>將它設得更低或完全不設時，則會保留既有的不正確行為。|
|範圍|不明|
|版本|4.8|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|

