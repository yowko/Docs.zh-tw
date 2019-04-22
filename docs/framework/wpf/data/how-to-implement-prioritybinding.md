---
title: HOW TO：實作 PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: aaf2caff1e2684e08c7eb65125536f1070203d70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207561"
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="03482-102">HOW TO：實作 PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="03482-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="03482-103"><xref:System.Windows.Data.PriorityBinding> 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的運作方式是指定繫結的清單。</span><span class="sxs-lookup"><span data-stu-id="03482-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="03482-104">繫結清單的順序是從最高優先順序到最低優先順序。</span><span class="sxs-lookup"><span data-stu-id="03482-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="03482-105">如果最高的優先權繫結傳回值已成功處理時就永遠不需要處理清單中的其他繫結。</span><span class="sxs-lookup"><span data-stu-id="03482-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="03482-106">它可能是最高的優先權繫結需要很長的時間，要評估的情況下，優先順序較高的繫結成功地傳回值之前，都會使用下一個最高優先順序成功地傳回值。</span><span class="sxs-lookup"><span data-stu-id="03482-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03482-107">範例</span><span class="sxs-lookup"><span data-stu-id="03482-107">Example</span></span>  
 <span data-ttu-id="03482-108">示範如何<xref:System.Windows.Data.PriorityBinding>運作`AsyncDataSource`物件已建立具有下列三個屬性： `FastDP`， `SlowerDP`，和`SlowestDP`。</span><span class="sxs-lookup"><span data-stu-id="03482-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="03482-109">Get 存取子`FastDP`傳回的值`_fastDP`資料成員。</span><span class="sxs-lookup"><span data-stu-id="03482-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="03482-110">Get 存取子`SlowerDP`等候 3 秒後，再傳回`_slowerDP`資料成員。</span><span class="sxs-lookup"><span data-stu-id="03482-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="03482-111">Get 存取子`SlowestDP`等候傳回的值之前的 5 秒`_slowestDP`資料成員。</span><span class="sxs-lookup"><span data-stu-id="03482-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03482-112">此範例僅供示範之用。</span><span class="sxs-lookup"><span data-stu-id="03482-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="03482-113">[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]指導方針，建議您不要定義速度較慢的欄位集合會比的屬性。</span><span class="sxs-lookup"><span data-stu-id="03482-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="03482-114">如需詳細資訊，請參閱 <<c0> [ 選擇之間的屬性和方法](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="03482-114">For more information, see [Choosing Between Properties and Methods](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span></span>  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="03482-115"><xref:System.Windows.Controls.TextBlock.Text%2A>屬性繫結至上述`AsyncDS`使用<xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="03482-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="03482-116">當繫結引擎會處理<xref:System.Windows.Data.Binding>物件，它的第一個開頭<xref:System.Windows.Data.Binding>，它繫結至`SlowestDP`屬性。</span><span class="sxs-lookup"><span data-stu-id="03482-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="03482-117">當這<xref:System.Windows.Data.Binding>是處理，它不會傳回值已成功因為它正在睡眠中 5 秒，因此下一步<xref:System.Windows.Data.Binding>處理項目。</span><span class="sxs-lookup"><span data-stu-id="03482-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="03482-118">下一步<xref:System.Windows.Data.Binding>不會傳回值已成功因為睡眠 3 秒。</span><span class="sxs-lookup"><span data-stu-id="03482-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="03482-119">然後，繫結引擎會移到下一步<xref:System.Windows.Data.Binding>項目，繫結至`FastDP`屬性。</span><span class="sxs-lookup"><span data-stu-id="03482-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="03482-120">這<xref:System.Windows.Data.Binding>傳回值 「 快速值 」。</span><span class="sxs-lookup"><span data-stu-id="03482-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="03482-121"><xref:System.Windows.Controls.TextBlock>現在會顯示 「 快速值 」 的值。</span><span class="sxs-lookup"><span data-stu-id="03482-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="03482-122">在 3 秒過後之後,`SlowerDP`屬性會傳回 「 較慢的值 」 的值。</span><span class="sxs-lookup"><span data-stu-id="03482-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="03482-123"><xref:System.Windows.Controls.TextBlock>接著會顯示 「 速度較慢的值 」 的值。</span><span class="sxs-lookup"><span data-stu-id="03482-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="03482-124">在 5 秒過後之後,`SlowestDP`屬性會傳回值 「 最慢值 」。</span><span class="sxs-lookup"><span data-stu-id="03482-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="03482-125">該繫結具有最高優先權，因為它會先列出。</span><span class="sxs-lookup"><span data-stu-id="03482-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="03482-126"><xref:System.Windows.Controls.TextBlock>現在會顯示 「 最慢值 」 的值。</span><span class="sxs-lookup"><span data-stu-id="03482-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="03482-127">請參閱<xref:System.Windows.Data.PriorityBinding>如需有關什麼會被視為成功的傳回值，從繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="03482-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03482-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03482-128">See also</span></span>

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [<span data-ttu-id="03482-129">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="03482-129">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="03482-130">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="03482-130">How-to Topics</span></span>](data-binding-how-to-topics.md)
