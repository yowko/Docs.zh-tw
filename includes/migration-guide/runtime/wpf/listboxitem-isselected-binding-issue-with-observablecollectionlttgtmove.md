---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620092"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="e09f5-101">ObservableCollection&lt;T&gt;.Move 的 ListBoxItem IsSelected 繫結問題</span><span class="sxs-lookup"><span data-stu-id="e09f5-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="e09f5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e09f5-102">Details</span></span>

<span data-ttu-id="e09f5-103">針對繫結至 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 且已選取項目的集合呼叫 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 或 <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)>，可能會在未來選取或取消選取 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 項目時導致不穩定的行為。</span><span class="sxs-lookup"><span data-stu-id="e09f5-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e09f5-104">建議</span><span class="sxs-lookup"><span data-stu-id="e09f5-104">Suggestion</span></span>

<span data-ttu-id="e09f5-105">呼叫 <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> 和 <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> 而不是 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 可解決此問題。</span><span class="sxs-lookup"><span data-stu-id="e09f5-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="e09f5-106">此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="e09f5-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="e09f5-107">名稱</span><span class="sxs-lookup"><span data-stu-id="e09f5-107">Name</span></span>    | <span data-ttu-id="e09f5-108">值</span><span class="sxs-lookup"><span data-stu-id="e09f5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e09f5-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e09f5-109">Scope</span></span>   |<span data-ttu-id="e09f5-110">Minor</span><span class="sxs-lookup"><span data-stu-id="e09f5-110">Minor</span></span>|
|<span data-ttu-id="e09f5-111">版本</span><span class="sxs-lookup"><span data-stu-id="e09f5-111">Version</span></span>|<span data-ttu-id="e09f5-112">4.5</span><span class="sxs-lookup"><span data-stu-id="e09f5-112">4.5</span></span>|
|<span data-ttu-id="e09f5-113">類型</span><span class="sxs-lookup"><span data-stu-id="e09f5-113">Type</span></span>|<span data-ttu-id="e09f5-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="e09f5-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e09f5-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e09f5-115">Affected APIs</span></span>

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
