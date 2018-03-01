---
title: "如何：實作 PriorityBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e6ab8826f2298a8660a85d739fbe3456374b476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="dd931-102">如何：實作 PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="dd931-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="dd931-103"><xref:System.Windows.Data.PriorityBinding>在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的運作方式是指定繫結的清單。</span><span class="sxs-lookup"><span data-stu-id="dd931-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="dd931-104">繫結清單被依優先順序從高到最低優先順序。</span><span class="sxs-lookup"><span data-stu-id="dd931-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="dd931-105">如果最高優先權繫結的傳回值已成功處理時就永遠不需要處理清單中的其他繫結。</span><span class="sxs-lookup"><span data-stu-id="dd931-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="dd931-106">這可能是最高的優先權繫結需要很長的時間進行評估的案例，優先順序較高的繫結成功傳回值之前，都會使用下一個最高優先順序成功傳回值。</span><span class="sxs-lookup"><span data-stu-id="dd931-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd931-107">範例</span><span class="sxs-lookup"><span data-stu-id="dd931-107">Example</span></span>  
 <span data-ttu-id="dd931-108">若要示範如何<xref:System.Windows.Data.PriorityBinding>運作方式、`AsyncDataSource`物件已建立具有下列三個屬性： `FastDP`， `SlowerDP`，和`SlowestDP`。</span><span class="sxs-lookup"><span data-stu-id="dd931-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="dd931-109">Get 存取子的`FastDP`傳回的值`_fastDP`資料成員。</span><span class="sxs-lookup"><span data-stu-id="dd931-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="dd931-110">Get 存取子的`SlowerDP`3 秒後再傳回的值會等到`_slowerDP`資料成員。</span><span class="sxs-lookup"><span data-stu-id="dd931-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="dd931-111">Get 存取子的`SlowestDP`等待 5 秒鐘，再傳回`_slowestDP`資料成員。</span><span class="sxs-lookup"><span data-stu-id="dd931-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd931-112">這個範例是僅針對示範目的。</span><span class="sxs-lookup"><span data-stu-id="dd931-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="dd931-113">[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]指導方針，建議您不要定義速度較慢比欄位集的屬性。</span><span class="sxs-lookup"><span data-stu-id="dd931-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="dd931-114">如需詳細資訊，請參閱[NIB： 選擇之間指定屬性和方法](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af)。</span><span class="sxs-lookup"><span data-stu-id="dd931-114">For more information, see [NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).</span></span>  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="dd931-115"><xref:System.Windows.Controls.TextBlock.Text%2A>屬性繫結至上述`AsyncDS`使用<xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="dd931-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="dd931-116">當繫結引擎處理<xref:System.Windows.Data.Binding>物件，與第一個啟動<xref:System.Windows.Data.Binding>，它繫結至`SlowestDP`屬性。</span><span class="sxs-lookup"><span data-stu-id="dd931-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="dd931-117">當這<xref:System.Windows.Data.Binding>是處理，但是不會傳回值已成功因為它正在睡眠中 5 秒，因此下一步<xref:System.Windows.Data.Binding>處理項目。</span><span class="sxs-lookup"><span data-stu-id="dd931-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="dd931-118">下一步<xref:System.Windows.Data.Binding>沒有傳回值已成功因為睡眠 3 秒。</span><span class="sxs-lookup"><span data-stu-id="dd931-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="dd931-119">繫結引擎，然後移到下一個<xref:System.Windows.Data.Binding>元素，其繫結至`FastDP`屬性。</span><span class="sxs-lookup"><span data-stu-id="dd931-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="dd931-120">這<xref:System.Windows.Data.Binding>傳回"Fast Value"的值。</span><span class="sxs-lookup"><span data-stu-id="dd931-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="dd931-121"><xref:System.Windows.Controls.TextBlock>現在會顯示 「 快速值 」 的值。</span><span class="sxs-lookup"><span data-stu-id="dd931-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="dd931-122">在 3 秒超過之後`SlowerDP`屬性會傳回值 「 速度較慢的值 」。</span><span class="sxs-lookup"><span data-stu-id="dd931-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="dd931-123"><xref:System.Windows.Controls.TextBlock>然後顯示值"慢 Value"。</span><span class="sxs-lookup"><span data-stu-id="dd931-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="dd931-124">在 5 秒超過之後`SlowestDP`屬性會傳回值 「 最慢的值 」。</span><span class="sxs-lookup"><span data-stu-id="dd931-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="dd931-125">因為它會先列出，該繫結具有最高優先權。</span><span class="sxs-lookup"><span data-stu-id="dd931-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="dd931-126"><xref:System.Windows.Controls.TextBlock>現在會顯示 「 最慢的值 」 的值。</span><span class="sxs-lookup"><span data-stu-id="dd931-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="dd931-127">請參閱<xref:System.Windows.Data.PriorityBinding>如需有關什麼被視為成功的傳回值，從繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="dd931-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd931-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd931-128">See Also</span></span>  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="dd931-129">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="dd931-129">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="dd931-130">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="dd931-130">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
