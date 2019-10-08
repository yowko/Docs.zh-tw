---
title: 優化效能：應用程式資源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 759d02afe1934d2ace4ed226d5d911db2d676d98
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005036"
---
# <a name="optimizing-performance-application-resources"></a><span data-ttu-id="715ea-102">優化效能：應用程式資源</span><span class="sxs-lookup"><span data-stu-id="715ea-102">Optimizing Performance: Application Resources</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="715ea-103">可讓您共用應用程式資源，如此一來，您就可以在相似類型的元素之間支援一致的外觀或行為。</span><span class="sxs-lookup"><span data-stu-id="715ea-103">allows you to share application resources so that you can support a consistent look or behavior across similar-typed elements.</span></span> <span data-ttu-id="715ea-104">本主題提供此區域中的幾項建議，可協助您改善應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="715ea-104">This topic provides a few recommendations in this area that can help you improve the performance of your applications.</span></span>  
  
 <span data-ttu-id="715ea-105">如需詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="715ea-105">For more information on resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
## <a name="sharing-resources"></a><span data-ttu-id="715ea-106">共用資源</span><span class="sxs-lookup"><span data-stu-id="715ea-106">Sharing resources</span></span>  
 <span data-ttu-id="715ea-107">如果您的應用程式使用自訂控制項，並在 <xref:System.Windows.ResourceDictionary> （或 XAML 資源）節點中定義資源，建議您在 <xref:System.Windows.Application> 或 @no__t 2 物件層級定義資源，或在自訂控制項的預設主題中加以定義。</span><span class="sxs-lookup"><span data-stu-id="715ea-107">If your application uses custom controls and defines resources in a <xref:System.Windows.ResourceDictionary> (or XAML Resources node), it is recommended that you either define the resources at the <xref:System.Windows.Application> or <xref:System.Windows.Window> object level, or define them in the default theme for the custom controls.</span></span> <span data-ttu-id="715ea-108">在自訂控制項的 <xref:System.Windows.ResourceDictionary> 中定義資源，會對該控制項的每個實例造成效能上的影響。</span><span class="sxs-lookup"><span data-stu-id="715ea-108">Defining resources in a custom control's <xref:System.Windows.ResourceDictionary> imposes a performance impact for every instance of that control.</span></span> <span data-ttu-id="715ea-109">例如，如果您有一項需要大量效能的筆刷作業定義為自訂控制項的資源定義以及自訂控制項的許多實例，應用程式的工作集就會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="715ea-109">For example, if you have performance-intensive brush operations defined as part of the resource definition of a custom control and many instances of the custom control, the application's working set will increase significantly.</span></span>  
  
 <span data-ttu-id="715ea-110">為了說明這一點，請考慮下列事項。</span><span class="sxs-lookup"><span data-stu-id="715ea-110">To illustrate this point, consider the following.</span></span> <span data-ttu-id="715ea-111">假設您正在使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 來開發撲克牌遊戲。</span><span class="sxs-lookup"><span data-stu-id="715ea-111">Let's say you are developing a card game using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="715ea-112">對於大部分的撲克牌遊戲，您需要52張具有52不同臉部的卡片。</span><span class="sxs-lookup"><span data-stu-id="715ea-112">For most card games, you need 52 cards with 52 different faces.</span></span> <span data-ttu-id="715ea-113">您決定要執行卡片自訂控制項，並在卡片自訂控制項的資源中定義52筆刷（每個都代表卡片臉部）。</span><span class="sxs-lookup"><span data-stu-id="715ea-113">You decide to implement a card custom control and you define 52 brushes (each representing a card face) in the resources of your card custom control.</span></span> <span data-ttu-id="715ea-114">在您的主要應用程式中，您一開始會建立此卡片自訂控制項的52實例。</span><span class="sxs-lookup"><span data-stu-id="715ea-114">In your main application, you initially create 52 instances of this card custom control.</span></span> <span data-ttu-id="715ea-115">卡片自訂控制項的每個實例都會產生 <xref:System.Windows.Media.Brush> 個物件的52實例，在您的應用程式中，總共提供 52 \* 52 <xref:System.Windows.Media.Brush> 個物件。</span><span class="sxs-lookup"><span data-stu-id="715ea-115">Each instance of the card custom control generates 52 instances of <xref:System.Windows.Media.Brush> objects, which gives you a total of 52 \* 52 <xref:System.Windows.Media.Brush> objects in your application.</span></span> <span data-ttu-id="715ea-116">將筆刷從卡片自訂控制項資源移到 <xref:System.Windows.Application> 或 @no__t 1 物件層級，或在自訂控制項的預設主題中加以定義，就會減少應用程式的工作集，因為您現在會在52之間共用52筆刷卡片控制項的實例。</span><span class="sxs-lookup"><span data-stu-id="715ea-116">By moving the brushes out of the card custom control resources to the <xref:System.Windows.Application> or <xref:System.Windows.Window> object level, or defining them in the default theme for the custom control, you reduce the working set of the application, since you are now sharing the 52 brushes among 52 instances of the card control.</span></span>  
  
## <a name="sharing-a-brush-without-copying"></a><span data-ttu-id="715ea-117">共用筆刷而不復制</span><span class="sxs-lookup"><span data-stu-id="715ea-117">Sharing a Brush without Copying</span></span>  
 <span data-ttu-id="715ea-118">如果您有多個使用相同 <xref:System.Windows.Media.Brush> 物件的元素，請將筆刷定義為資源並加以參考，而不是在 XAML 中定義筆刷內嵌。</span><span class="sxs-lookup"><span data-stu-id="715ea-118">If you have multiple elements using the same <xref:System.Windows.Media.Brush> object, define the brush as a resource and reference it, rather than defining the brush inline in XAML.</span></span> <span data-ttu-id="715ea-119">這個方法會建立一個實例並重複使用它，而在 XAML 中定義以內嵌的筆刷會針對每個專案建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="715ea-119">This method will create one instance and reuse it, whereas defining brushes inline in XAML creates a new instance for each element.</span></span>  
  
 <span data-ttu-id="715ea-120">下列標記範例說明這一點：</span><span class="sxs-lookup"><span data-stu-id="715ea-120">The following markup sample illustrates this point:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a><span data-ttu-id="715ea-121">盡可能使用靜態資源</span><span class="sxs-lookup"><span data-stu-id="715ea-121">Use Static Resources when Possible</span></span>  
 <span data-ttu-id="715ea-122">靜態資源會藉由查閱已定義資源的參考，提供任何 XAML 屬性屬性的值。</span><span class="sxs-lookup"><span data-stu-id="715ea-122">A static resource provides a value for any XAML property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="715ea-123">該資源的查閱行為類似于編譯時間查閱。</span><span class="sxs-lookup"><span data-stu-id="715ea-123">Lookup behavior for that resource is analogous to compile-time lookup.</span></span>  
  
 <span data-ttu-id="715ea-124">另一方面，動態資源會在初始編譯期間建立暫存運算式，因此會延遲資源的查閱，直到實際需要要求的資源值才能建立物件為止。</span><span class="sxs-lookup"><span data-stu-id="715ea-124">A dynamic resource, on the other hand, will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="715ea-125">該資源的查閱行為類似于執行時間查詢，這會影響效能。</span><span class="sxs-lookup"><span data-stu-id="715ea-125">Lookup behavior for that resource is analogous to run-time lookup, which imposes a performance impact.</span></span> <span data-ttu-id="715ea-126">請盡可能在您的應用程式中使用靜態資源，只有在必要時才使用動態資源。</span><span class="sxs-lookup"><span data-stu-id="715ea-126">Use static resources whenever possible in your application, using dynamic resources only when necessary.</span></span>  
  
 <span data-ttu-id="715ea-127">下列標記範例示範如何使用這兩種類型的資源：</span><span class="sxs-lookup"><span data-stu-id="715ea-127">The following markup sample shows the use of both types of resources:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a><span data-ttu-id="715ea-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="715ea-128">See also</span></span>

- [<span data-ttu-id="715ea-129">最佳化 WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="715ea-129">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="715ea-130">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="715ea-130">Planning for Application Performance</span></span>](planning-for-application-performance.md)
- [<span data-ttu-id="715ea-131">運用硬體</span><span class="sxs-lookup"><span data-stu-id="715ea-131">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)
- [<span data-ttu-id="715ea-132">版面配置與設計</span><span class="sxs-lookup"><span data-stu-id="715ea-132">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)
- [<span data-ttu-id="715ea-133">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="715ea-133">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="715ea-134">物件行為</span><span class="sxs-lookup"><span data-stu-id="715ea-134">Object Behavior</span></span>](optimizing-performance-object-behavior.md)
- [<span data-ttu-id="715ea-135">Text</span><span class="sxs-lookup"><span data-stu-id="715ea-135">Text</span></span>](optimizing-performance-text.md)
- [<span data-ttu-id="715ea-136">資料繫結</span><span class="sxs-lookup"><span data-stu-id="715ea-136">Data Binding</span></span>](optimizing-performance-data-binding.md)
- [<span data-ttu-id="715ea-137">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="715ea-137">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)
