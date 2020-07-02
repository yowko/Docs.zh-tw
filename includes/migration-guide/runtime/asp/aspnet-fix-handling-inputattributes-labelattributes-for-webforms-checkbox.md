---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621947"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="1f131-101">ASP.NET 修正 WebForms CheckBox 控制項的 InputAttributes 和 LabelAttributes 處理方式</span><span class="sxs-lookup"><span data-stu-id="1f131-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="1f131-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1f131-102">Details</span></span>

<span data-ttu-id="1f131-103">若應用程式是以 .NET Framework 4.7.2 和更早版本為目標，回傳後會遺失以程式設計方式新增至 WebForms <xref:System.Web.UI.WebControls.CheckBox> 控制項的 <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> 和 <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1f131-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="1f131-104">若應用程式是以 .NET Framework 4.8 或更新版本為目標，則回傳後仍會保留這些項目。</span><span class="sxs-lookup"><span data-stu-id="1f131-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1f131-105">建議</span><span class="sxs-lookup"><span data-stu-id="1f131-105">Suggestion</span></span>

<span data-ttu-id="1f131-106">為了確保回傳時還原屬性的正確行為，請將 <code>targetFrameworkVersion</code> 設為 4.8 或更高。</span><span class="sxs-lookup"><span data-stu-id="1f131-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="1f131-107">例如：</span><span class="sxs-lookup"><span data-stu-id="1f131-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="1f131-108">將它設得更低或完全不設時，則會保留既有的不正確行為。</span><span class="sxs-lookup"><span data-stu-id="1f131-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="1f131-109">名稱</span><span class="sxs-lookup"><span data-stu-id="1f131-109">Name</span></span>    | <span data-ttu-id="1f131-110">值</span><span class="sxs-lookup"><span data-stu-id="1f131-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1f131-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="1f131-111">Scope</span></span>   |<span data-ttu-id="1f131-112">Unknown</span><span class="sxs-lookup"><span data-stu-id="1f131-112">Unknown</span></span>|
|<span data-ttu-id="1f131-113">版本</span><span class="sxs-lookup"><span data-stu-id="1f131-113">Version</span></span>|<span data-ttu-id="1f131-114">4.8</span><span class="sxs-lookup"><span data-stu-id="1f131-114">4.8</span></span>|
|<span data-ttu-id="1f131-115">類型</span><span class="sxs-lookup"><span data-stu-id="1f131-115">Type</span></span>|<span data-ttu-id="1f131-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="1f131-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f131-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1f131-117">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
