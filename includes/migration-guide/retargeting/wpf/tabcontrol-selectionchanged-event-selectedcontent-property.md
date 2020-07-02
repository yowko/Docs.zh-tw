---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614607"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a><span data-ttu-id="480a1-101">TabControl SelectionChanged 事件和 SelectedContent 屬性</span><span class="sxs-lookup"><span data-stu-id="480a1-101">TabControl SelectionChanged event and SelectedContent property</span></span>

#### <a name="details"></a><span data-ttu-id="480a1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="480a1-102">Details</span></span>

<span data-ttu-id="480a1-103">從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.TabControl> 會在其選取項目變更時先更新其 <xref:System.Windows.Controls.TabControl.SelectedContent> 屬性的值，再引發 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件。在 .NET Framework 4.7 和舊版中，更新 SelectedContent 發生在事件之後。</span><span class="sxs-lookup"><span data-stu-id="480a1-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.TabControl> updates the value of its <xref:System.Windows.Controls.TabControl.SelectedContent> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.In the .NET Framework 4.7 and earlier versions, the update to SelectedContent happened after the event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="480a1-104">建議</span><span class="sxs-lookup"><span data-stu-id="480a1-104">Suggestion</span></span>

<span data-ttu-id="480a1-105">以 .NET Framework 4.7.1 或更新版本為目標的應用程式可透過在應用程式組態檔的 `<runtime>` 區段中新增下列內容來選擇退出此變更，並使用舊版行為：</span><span class="sxs-lookup"><span data-stu-id="480a1-105">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="480a1-106">以 .NET Framework 4.7 或舊版為目標但在 .NET Framework 4.7.1 或更新版本上執行的應用程式，只要在應用程式組態檔的 `<runtime>` 區段新增下列程式行，就能啟用新行為：</span><span class="sxs-lookup"><span data-stu-id="480a1-106">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="480a1-107">名稱</span><span class="sxs-lookup"><span data-stu-id="480a1-107">Name</span></span>    | <span data-ttu-id="480a1-108">值</span><span class="sxs-lookup"><span data-stu-id="480a1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="480a1-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="480a1-109">Scope</span></span>   | <span data-ttu-id="480a1-110">Minor</span><span class="sxs-lookup"><span data-stu-id="480a1-110">Minor</span></span>       |
| <span data-ttu-id="480a1-111">版本</span><span class="sxs-lookup"><span data-stu-id="480a1-111">Version</span></span> | <span data-ttu-id="480a1-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="480a1-112">4.7.1</span></span>       |
| <span data-ttu-id="480a1-113">類型</span><span class="sxs-lookup"><span data-stu-id="480a1-113">Type</span></span>    | <span data-ttu-id="480a1-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="480a1-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="480a1-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="480a1-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
