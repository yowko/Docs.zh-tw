---
title: 作法：實作 PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: ad19db9d686469e3ade1ff188553fceb8d525674
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937438"
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="e31d5-102">作法：實作 PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="e31d5-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="e31d5-103"><xref:System.Windows.Data.PriorityBinding>在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] [運作方式] 中, 指定系結的清單。</span><span class="sxs-lookup"><span data-stu-id="e31d5-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="e31d5-104">系結清單的排序次序是從最高優先順序到最低優先順序。</span><span class="sxs-lookup"><span data-stu-id="e31d5-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="e31d5-105">如果在處理時, 最高優先順序的系結成功傳回值, 則不需要處理清單中的其他系結。</span><span class="sxs-lookup"><span data-stu-id="e31d5-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="e31d5-106">可能是最高優先順序的系結需要較長的時間才能進行評估, 則會使用成功傳回值的下一個最高優先順序, 直到較高優先權的系結成功傳回值為止。</span><span class="sxs-lookup"><span data-stu-id="e31d5-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e31d5-107">範例</span><span class="sxs-lookup"><span data-stu-id="e31d5-107">Example</span></span>  
 <span data-ttu-id="e31d5-108">為了示範如何<xref:System.Windows.Data.PriorityBinding>運作`AsyncDataSource` , 已使用下列三個屬性建立物件: `FastDP`、 `SlowerDP`和`SlowestDP`。</span><span class="sxs-lookup"><span data-stu-id="e31d5-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="e31d5-109">的 get 存取`FastDP`子會傳回`_fastDP`資料成員的值。</span><span class="sxs-lookup"><span data-stu-id="e31d5-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="e31d5-110">Get 存取`SlowerDP`子會等候3秒, 然後才傳回`_slowerDP`資料成員的值。</span><span class="sxs-lookup"><span data-stu-id="e31d5-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="e31d5-111">Get 存取`SlowestDP`子會等待5秒, 然後才傳回`_slowestDP`資料成員的值。</span><span class="sxs-lookup"><span data-stu-id="e31d5-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e31d5-112">此範例僅供示範之用。</span><span class="sxs-lookup"><span data-stu-id="e31d5-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="e31d5-113">本[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]指導方針建議您不要定義的屬性, 其速度比欄位集還慢。</span><span class="sxs-lookup"><span data-stu-id="e31d5-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="e31d5-114">如需詳細資訊, 請參閱[在屬性和方法之間選擇](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e31d5-114">For more information, see [Choosing Between Properties and Methods](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span></span>  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="e31d5-115">屬性會`AsyncDS` 使用<xref:System.Windows.Data.PriorityBinding>系結至上述的: <xref:System.Windows.Controls.TextBlock.Text%2A></span><span class="sxs-lookup"><span data-stu-id="e31d5-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="e31d5-116">當系結引擎處理<xref:System.Windows.Data.Binding>物件時, 它會以第一個<xref:System.Windows.Data.Binding>系結至`SlowestDP`屬性的開始。</span><span class="sxs-lookup"><span data-stu-id="e31d5-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="e31d5-117">當處理<xref:System.Windows.Data.Binding>這個時, 它不會成功傳回值, 因為它會進入5秒的睡眠狀態, 因此<xref:System.Windows.Data.Binding>會處理下一個元素。</span><span class="sxs-lookup"><span data-stu-id="e31d5-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="e31d5-118">下一個<xref:System.Windows.Data.Binding>未成功傳回值, 因為它正在睡眠3秒。</span><span class="sxs-lookup"><span data-stu-id="e31d5-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="e31d5-119">然後, 系結引擎會移至<xref:System.Windows.Data.Binding>下一個系結`FastDP`至屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="e31d5-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="e31d5-120">這<xref:System.Windows.Data.Binding>會傳回值「快速值」。</span><span class="sxs-lookup"><span data-stu-id="e31d5-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="e31d5-121"><xref:System.Windows.Controls.TextBlock>現在會顯示值「快速值」。</span><span class="sxs-lookup"><span data-stu-id="e31d5-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="e31d5-122">經過3秒後, `SlowerDP`屬性會傳回值「較慢的值」。</span><span class="sxs-lookup"><span data-stu-id="e31d5-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="e31d5-123"><xref:System.Windows.Controls.TextBlock>然後會顯示值「較慢的值」。</span><span class="sxs-lookup"><span data-stu-id="e31d5-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="e31d5-124">經過5秒之後, `SlowestDP`屬性會傳回值「最慢的值」。</span><span class="sxs-lookup"><span data-stu-id="e31d5-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="e31d5-125">該系結具有最高的優先順序, 因為它會先列出。</span><span class="sxs-lookup"><span data-stu-id="e31d5-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="e31d5-126"><xref:System.Windows.Controls.TextBlock>現在會顯示值「最慢的值」。</span><span class="sxs-lookup"><span data-stu-id="e31d5-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="e31d5-127">如<xref:System.Windows.Data.PriorityBinding>需從系結中被視為成功傳回值的相關資訊, 請參閱。</span><span class="sxs-lookup"><span data-stu-id="e31d5-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31d5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e31d5-128">See also</span></span>

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e31d5-129">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="e31d5-129">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="e31d5-130">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="e31d5-130">How-to Topics</span></span>](data-binding-how-to-topics.md)
