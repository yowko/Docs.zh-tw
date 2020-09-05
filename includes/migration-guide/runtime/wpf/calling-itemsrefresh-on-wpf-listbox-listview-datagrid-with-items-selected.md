---
ms.openlocfilehash: 972601874d80d82ebae8b79779acfed82e5570cb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497131"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a><span data-ttu-id="f9fa8-101">在已選取項目的 WPF ListBox、ListView 或 DataGrid 上呼叫 Items.Refresh 會導致在項目中出現重複的項目</span><span class="sxs-lookup"><span data-stu-id="f9fa8-101">Calling Items.Refresh on a WPF ListBox, ListView, or DataGrid with items selected can cause duplicate items to appear in the element</span></span>

#### <a name="details"></a><span data-ttu-id="f9fa8-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f9fa8-102">Details</span></span>

<span data-ttu-id="f9fa8-103">在 .NET Framework 4.5 中，如果 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 中已選取項目，從程式碼呼叫 ListBox.Items.Refresh 可能會導致選取的項目在清單中重複出現。</span><span class="sxs-lookup"><span data-stu-id="f9fa8-103">In the .NET Framework 4.5, calling ListBox.Items.Refresh from code while items are selected in a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> can cause the selected items to be duplicated in the list.</span></span> <span data-ttu-id="f9fa8-104"><xref:System.Windows.Controls.ListView?displayProperty=fullName> 和 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 會發生類似的問題。</span><span class="sxs-lookup"><span data-stu-id="f9fa8-104">A similar issue occurs with <xref:System.Windows.Controls.ListView?displayProperty=fullName> and <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>.</span></span> <span data-ttu-id="f9fa8-105">這在 .NET Framework 4.6 中已修正。</span><span class="sxs-lookup"><span data-stu-id="f9fa8-105">This is fixed in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f9fa8-106">建議</span><span class="sxs-lookup"><span data-stu-id="f9fa8-106">Suggestion</span></span>

<span data-ttu-id="f9fa8-107">您可以在呼叫 <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> 之前以程式設計方式取消選取項目，然後在呼叫完成之後重新選取項目來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="f9fa8-107">This issue may be worked around by programmatically unselecting items before <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> is called and then re-selecting them after the call is completed.</span></span> <span data-ttu-id="f9fa8-108">此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="f9fa8-108">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="f9fa8-109">名稱</span><span class="sxs-lookup"><span data-stu-id="f9fa8-109">Name</span></span>    | <span data-ttu-id="f9fa8-110">值</span><span class="sxs-lookup"><span data-stu-id="f9fa8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f9fa8-111">範圍</span><span class="sxs-lookup"><span data-stu-id="f9fa8-111">Scope</span></span>   |<span data-ttu-id="f9fa8-112">Minor</span><span class="sxs-lookup"><span data-stu-id="f9fa8-112">Minor</span></span>|
|<span data-ttu-id="f9fa8-113">版本</span><span class="sxs-lookup"><span data-stu-id="f9fa8-113">Version</span></span>|<span data-ttu-id="f9fa8-114">4.5</span><span class="sxs-lookup"><span data-stu-id="f9fa8-114">4.5</span></span>|
|<span data-ttu-id="f9fa8-115">類型</span><span class="sxs-lookup"><span data-stu-id="f9fa8-115">Type</span></span>|<span data-ttu-id="f9fa8-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="f9fa8-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f9fa8-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f9fa8-117">Affected APIs</span></span>

- <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Data.CollectionView.Refresh`

-->
