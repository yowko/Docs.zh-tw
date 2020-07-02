---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614599"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a><span data-ttu-id="e1938-101">Selector 的 SelectionChanged 事件和 SelectedValue 屬性</span><span class="sxs-lookup"><span data-stu-id="e1938-101">Selector SelectionChanged event and SelectedValue property</span></span>

#### <a name="details"></a><span data-ttu-id="e1938-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1938-102">Details</span></span>

<span data-ttu-id="e1938-103">從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.Primitives.Selector> 在其選取項目變更時，一律會先更新其 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性的值，再引發 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="e1938-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> always updates the value of its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.</span></span> <span data-ttu-id="e1938-104">這會讓 SelectedValue 屬性與其他的選取項目屬性一致 (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> 和 <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>)，它們會在引發事件前予以更新。</span><span class="sxs-lookup"><span data-stu-id="e1938-104">This makes the SelectedValue property consistent with the other selection properties (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> and <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), which are updated before raising the event.</span></span><p/><span data-ttu-id="e1938-105">在 .NET Framework 4.7 和舊版中，在大部分情況下，更新 SelectedValue 會發生在事件之前，但如果選取項目變更是由於變更 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性所造成，則會發生在事件之後。</span><span class="sxs-lookup"><span data-stu-id="e1938-105">In the .NET Framework 4.7 and earlier versions, the update to SelectedValue happened before the event in most cases, but it happened after the event if the selection change was caused by changing the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e1938-106">建議</span><span class="sxs-lookup"><span data-stu-id="e1938-106">Suggestion</span></span>

<span data-ttu-id="e1938-107">以 .NET Framework 4.7.1 或更新版本為目標的應用程式可透過在應用程式組態檔的 `<runtime>` 區段中新增下列內容來選擇退出此變更，並使用舊版行為：</span><span class="sxs-lookup"><span data-stu-id="e1938-107">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="e1938-108">以 .NET Framework 4.7 或舊版為目標但在 .NET Framework 4.7.1 或更新版本上執行的應用程式，只要在應用程式組態檔的 `<runtime>` 區段新增下列程式行，就能啟用新行為：</span><span class="sxs-lookup"><span data-stu-id="e1938-108">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e1938-109">名稱</span><span class="sxs-lookup"><span data-stu-id="e1938-109">Name</span></span>    | <span data-ttu-id="e1938-110">值</span><span class="sxs-lookup"><span data-stu-id="e1938-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e1938-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e1938-111">Scope</span></span>   | <span data-ttu-id="e1938-112">Minor</span><span class="sxs-lookup"><span data-stu-id="e1938-112">Minor</span></span>       |
| <span data-ttu-id="e1938-113">版本</span><span class="sxs-lookup"><span data-stu-id="e1938-113">Version</span></span> | <span data-ttu-id="e1938-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="e1938-114">4.7.1</span></span>       |
| <span data-ttu-id="e1938-115">類型</span><span class="sxs-lookup"><span data-stu-id="e1938-115">Type</span></span>    | <span data-ttu-id="e1938-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="e1938-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e1938-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e1938-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
