---
ms.openlocfilehash: 196b6a13d32c7767b858d6d68ca775eb49324805
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497217"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="03fb7-101">ObservableCollection&lt;T&gt;.Move 的 ListBoxItem IsSelected 繫結問題</span><span class="sxs-lookup"><span data-stu-id="03fb7-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="03fb7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="03fb7-102">Details</span></span>

<span data-ttu-id="03fb7-103">針對繫結至 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 且已選取項目的集合呼叫 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 或 <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)>，可能會在未來選取或取消選取 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 項目時導致不穩定的行為。</span><span class="sxs-lookup"><span data-stu-id="03fb7-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="03fb7-104">建議</span><span class="sxs-lookup"><span data-stu-id="03fb7-104">Suggestion</span></span>

<span data-ttu-id="03fb7-105">呼叫 <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> 和 <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> 而不是 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 可解決此問題。</span><span class="sxs-lookup"><span data-stu-id="03fb7-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="03fb7-106">此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="03fb7-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="03fb7-107">名稱</span><span class="sxs-lookup"><span data-stu-id="03fb7-107">Name</span></span>    | <span data-ttu-id="03fb7-108">值</span><span class="sxs-lookup"><span data-stu-id="03fb7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="03fb7-109">範圍</span><span class="sxs-lookup"><span data-stu-id="03fb7-109">Scope</span></span>   |<span data-ttu-id="03fb7-110">Minor</span><span class="sxs-lookup"><span data-stu-id="03fb7-110">Minor</span></span>|
|<span data-ttu-id="03fb7-111">版本</span><span class="sxs-lookup"><span data-stu-id="03fb7-111">Version</span></span>|<span data-ttu-id="03fb7-112">4.5</span><span class="sxs-lookup"><span data-stu-id="03fb7-112">4.5</span></span>|
|<span data-ttu-id="03fb7-113">類型</span><span class="sxs-lookup"><span data-stu-id="03fb7-113">Type</span></span>|<span data-ttu-id="03fb7-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="03fb7-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="03fb7-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="03fb7-115">Affected APIs</span></span>

- <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.ObjectModel.ObservableCollection`1.Move(System.Int32,System.Int32)``
- ``M:System.Collections.ObjectModel.ObservableCollection`1.MoveItem(System.Int32,System.Int32)``

-->
