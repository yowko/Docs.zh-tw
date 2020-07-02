---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614602"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a><span data-ttu-id="bd882-101">鍵盤焦點現在可在 WinForms/WPF 裝載的多個圖層中正確移動</span><span class="sxs-lookup"><span data-stu-id="bd882-101">Keyboard focus now moves correctly across multiple layers of WinForms/WPF hosting</span></span>

#### <a name="details"></a><span data-ttu-id="bd882-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bd882-102">Details</span></span>

<span data-ttu-id="bd882-103">請考慮裝載 WinForms 控制項的 WPF 應用程式，此控制項因此會裝載 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="bd882-103">Consider a WPF application hosting a WinForms control which in turn hosts WPF controls.</span></span> <span data-ttu-id="bd882-104">如果該圖層中的第一個或最後一個控制項是 WPF `System.Windows.Forms.Integration.ElementHost`，使用者可能無法使用 Tab 離開 WinForms 圖層。</span><span class="sxs-lookup"><span data-stu-id="bd882-104">Users may not be able to tab out of the WinForms layer if the first or last control in that layer is the WPF `System.Windows.Forms.Integration.ElementHost`.</span></span> <span data-ttu-id="bd882-105">這項變更會修正此問題，而且使用者現在可以使用 Tab 離開 WinForms 圖層。依賴焦點的自動化應用程式絕不會逸出可能不再如預期運作的 WinForms 圖層。</span><span class="sxs-lookup"><span data-stu-id="bd882-105">This change fixes this issue, and users are now able to tab out of the WinForms layer.Automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bd882-106">建議</span><span class="sxs-lookup"><span data-stu-id="bd882-106">Suggestion</span></span>

<span data-ttu-id="bd882-107">至於以低於 .NET Framework 4.7.2 版本為目標，又想要利用這項變更的開發人員，可以將下列 AppContext 旗標集合設為 false，以啟用變更。</span><span class="sxs-lookup"><span data-stu-id="bd882-107">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 can set the following set of AppContext flags to false for the change to be enabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="bd882-108">WPF 應用程式必須選擇所有早期的協助工具改善，才能取得更新版本的增強功能。</span><span class="sxs-lookup"><span data-stu-id="bd882-108">WPF applications must opt in to all early accessibility improvements to get the later improvements.</span></span> <span data-ttu-id="bd882-109">換句話說，`Switch.UseLegacyAccessibilityFeatures` 和 `Switch.UseLegacyAccessibilityFeatures.2` 參數都必須是以 .NET 4.7.2 或更新版本為目標且需要先前功能的 setA 開發人員，其可將下列的 AppContext 旗標設為 true，才能停用變更。</span><span class="sxs-lookup"><span data-stu-id="bd882-109">In other words, both the `Switch.UseLegacyAccessibilityFeatures` and the `Switch.UseLegacyAccessibilityFeatures.2` switches must be setA developer who requires the previous functionality while targeting .NET 4.7.2 or greater can set the following AppContext flag to true for the change to be disabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="bd882-110">名稱</span><span class="sxs-lookup"><span data-stu-id="bd882-110">Name</span></span>    | <span data-ttu-id="bd882-111">值</span><span class="sxs-lookup"><span data-stu-id="bd882-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bd882-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="bd882-112">Scope</span></span>   | <span data-ttu-id="bd882-113">Edge</span><span class="sxs-lookup"><span data-stu-id="bd882-113">Edge</span></span>        |
| <span data-ttu-id="bd882-114">版本</span><span class="sxs-lookup"><span data-stu-id="bd882-114">Version</span></span> | <span data-ttu-id="bd882-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="bd882-115">4.7.2</span></span>       |
| <span data-ttu-id="bd882-116">類型</span><span class="sxs-lookup"><span data-stu-id="bd882-116">Type</span></span>    | <span data-ttu-id="bd882-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="bd882-117">Retargeting</span></span> |
