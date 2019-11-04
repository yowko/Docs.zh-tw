---
title: 如何：實作 PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459791"
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="272c4-102">如何：實作 PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="272c4-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="272c4-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 <xref:System.Windows.Data.PriorityBinding> 會藉由指定系結的清單來運作。</span><span class="sxs-lookup"><span data-stu-id="272c4-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="272c4-104">系結清單的排序次序是從最高優先順序到最低優先順序。</span><span class="sxs-lookup"><span data-stu-id="272c4-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="272c4-105">如果在處理時，最高優先順序的系結成功傳回值，則不需要處理清單中的其他系結。</span><span class="sxs-lookup"><span data-stu-id="272c4-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="272c4-106">可能是最高優先順序的系結需要較長的時間才能進行評估，則會使用成功傳回值的下一個最高優先順序，直到較高優先權的系結成功傳回值為止。</span><span class="sxs-lookup"><span data-stu-id="272c4-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="272c4-107">範例</span><span class="sxs-lookup"><span data-stu-id="272c4-107">Example</span></span>  
 <span data-ttu-id="272c4-108">為了示範 <xref:System.Windows.Data.PriorityBinding> 的運作方式，已建立具有下列三個屬性的 `AsyncDataSource` 物件： `FastDP`、`SlowerDP`和 `SlowestDP`。</span><span class="sxs-lookup"><span data-stu-id="272c4-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="272c4-109">`FastDP` 的 get 存取子會傳回 `_fastDP` 資料成員的值。</span><span class="sxs-lookup"><span data-stu-id="272c4-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="272c4-110">`SlowerDP` 的 get 存取子會等待3秒，再傳回 `_slowerDP` 資料成員的值。</span><span class="sxs-lookup"><span data-stu-id="272c4-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="272c4-111">`SlowestDP` 的 get 存取子會等待5秒，再傳回 `_slowestDP` 資料成員的值。</span><span class="sxs-lookup"><span data-stu-id="272c4-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="272c4-112">此範例僅供示範之用。</span><span class="sxs-lookup"><span data-stu-id="272c4-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="272c4-113">.NET 指導方針建議定義的屬性，其速度比欄位集還慢。</span><span class="sxs-lookup"><span data-stu-id="272c4-113">The .NET guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="272c4-114">如需詳細資訊，請參閱[在屬性和方法之間選擇](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="272c4-114">For more information, see [Choosing Between Properties and Methods](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span></span>  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="272c4-115"><xref:System.Windows.Controls.TextBlock.Text%2A> 屬性會使用 <xref:System.Windows.Data.PriorityBinding>系結至上述 `AsyncDS`：</span><span class="sxs-lookup"><span data-stu-id="272c4-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="272c4-116">當系結引擎處理 <xref:System.Windows.Data.Binding> 物件時，它會從系結至 `SlowestDP` 屬性的第一個 <xref:System.Windows.Data.Binding>開始。</span><span class="sxs-lookup"><span data-stu-id="272c4-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="272c4-117">處理此 <xref:System.Windows.Data.Binding> 時，它不會成功傳回值，因為它正在睡眠5秒，因此會處理下一個 <xref:System.Windows.Data.Binding> 元素。</span><span class="sxs-lookup"><span data-stu-id="272c4-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="272c4-118">下一個 <xref:System.Windows.Data.Binding> 未成功傳回值，因為它正在睡眠3秒。</span><span class="sxs-lookup"><span data-stu-id="272c4-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="272c4-119">然後，系結引擎會移至下一個系結至 `FastDP` 屬性的 <xref:System.Windows.Data.Binding> 元素。</span><span class="sxs-lookup"><span data-stu-id="272c4-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="272c4-120">此 <xref:System.Windows.Data.Binding> 會傳回值「快速值」。</span><span class="sxs-lookup"><span data-stu-id="272c4-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="272c4-121"><xref:System.Windows.Controls.TextBlock> 現在會顯示值「快速值」。</span><span class="sxs-lookup"><span data-stu-id="272c4-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="272c4-122">經過3秒之後，`SlowerDP` 屬性會傳回值「較慢的值」。</span><span class="sxs-lookup"><span data-stu-id="272c4-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="272c4-123">然後，<xref:System.Windows.Controls.TextBlock> 會顯示「較慢的值」值。</span><span class="sxs-lookup"><span data-stu-id="272c4-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="272c4-124">經過5秒之後，`SlowestDP` 屬性會傳回值「最慢的值」。</span><span class="sxs-lookup"><span data-stu-id="272c4-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="272c4-125">該系結具有最高的優先順序，因為它會先列出。</span><span class="sxs-lookup"><span data-stu-id="272c4-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="272c4-126"><xref:System.Windows.Controls.TextBlock> 現在會顯示值「最慢的值」。</span><span class="sxs-lookup"><span data-stu-id="272c4-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="272c4-127">如需從系結中被視為成功傳回值的相關資訊，請參閱 <xref:System.Windows.Data.PriorityBinding>。</span><span class="sxs-lookup"><span data-stu-id="272c4-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272c4-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="272c4-128">See also</span></span>

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [<span data-ttu-id="272c4-129">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="272c4-129">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="272c4-130">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="272c4-130">How-to Topics</span></span>](data-binding-how-to-topics.md)
