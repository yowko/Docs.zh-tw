---
ms.openlocfilehash: e605e0f2636d83745815ec4ed27bf72692f18d15
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802639"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="0fc34-101">ASP.NET 修正 WebForms CheckBox 控制項的 InputAttributes 和 LabelAttributes 處理方式</span><span class="sxs-lookup"><span data-stu-id="0fc34-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0fc34-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0fc34-102">Details</span></span>|<span data-ttu-id="0fc34-103">若應用程式是以 .NET Framework 4.7.2 和更早版本為目標，回傳後會遺失以程式設計方式新增至 WebForms <xref:System.Web.UI.WebControls.CheckBox> 控制項的 <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> 和 <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0fc34-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="0fc34-104">若應用程式是以 .NET Framework 4.8 或更新版本為目標，則回傳後仍會保留這些項目。</span><span class="sxs-lookup"><span data-stu-id="0fc34-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>|
|<span data-ttu-id="0fc34-105">建議</span><span class="sxs-lookup"><span data-stu-id="0fc34-105">Suggestion</span></span>|<span data-ttu-id="0fc34-106">為了確保回傳時還原屬性的正確行為，請將 <code>targetFrameworkVersion</code> 設為 4.8 或更高。</span><span class="sxs-lookup"><span data-stu-id="0fc34-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="0fc34-107">例如：</span><span class="sxs-lookup"><span data-stu-id="0fc34-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="0fc34-108">將它設得更低或完全不設時，則會保留既有的不正確行為。</span><span class="sxs-lookup"><span data-stu-id="0fc34-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>|
|<span data-ttu-id="0fc34-109">範圍</span><span class="sxs-lookup"><span data-stu-id="0fc34-109">Scope</span></span>|<span data-ttu-id="0fc34-110">不明</span><span class="sxs-lookup"><span data-stu-id="0fc34-110">Unknown</span></span>|
|<span data-ttu-id="0fc34-111">版本</span><span class="sxs-lookup"><span data-stu-id="0fc34-111">Version</span></span>|<span data-ttu-id="0fc34-112">4.8</span><span class="sxs-lookup"><span data-stu-id="0fc34-112">4.8</span></span>|
|<span data-ttu-id="0fc34-113">類型</span><span class="sxs-lookup"><span data-stu-id="0fc34-113">Type</span></span>|<span data-ttu-id="0fc34-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="0fc34-114">Runtime</span></span>|
|<span data-ttu-id="0fc34-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0fc34-115">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|

