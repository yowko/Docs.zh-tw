---
title: 最佳化效能：應用程式資源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 921a67a24464ff5ac782045ae022f7766f32d579
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352395"
---
# <a name="optimizing-performance-application-resources"></a><span data-ttu-id="ca896-102">最佳化效能：應用程式資源</span><span class="sxs-lookup"><span data-stu-id="ca896-102">Optimizing Performance: Application Resources</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="ca896-103">可讓您共用應用程式資源，以便您可以透過類似類型的項目支援一致的外觀或行為。</span><span class="sxs-lookup"><span data-stu-id="ca896-103">allows you to share application resources so that you can support a consistent look or behavior across similar-typed elements.</span></span> <span data-ttu-id="ca896-104">本主題提供可協助您這方面的一些建議改善您的應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="ca896-104">This topic provides a few recommendations in this area that can help you improve the performance of your applications.</span></span>  
  
 <span data-ttu-id="ca896-105">如需詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="ca896-105">For more information on resources, see [XAML Resources](xaml-resources.md).</span></span>  
  
## <a name="sharing-resources"></a><span data-ttu-id="ca896-106">共用資源</span><span class="sxs-lookup"><span data-stu-id="ca896-106">Sharing resources</span></span>  
 <span data-ttu-id="ca896-107">如果您的應用程式會使用自訂控制項，並定義中的資源<xref:System.Windows.ResourceDictionary>（或 XAML 資源節點），建議您其中一個定義的資源<xref:System.Windows.Application>或<xref:System.Windows.Window>物件層級，或定義中的預設佈景主題自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="ca896-107">If your application uses custom controls and defines resources in a <xref:System.Windows.ResourceDictionary> (or XAML Resources node), it is recommended that you either define the resources at the <xref:System.Windows.Application> or <xref:System.Windows.Window> object level, or define them in the default theme for the custom controls.</span></span> <span data-ttu-id="ca896-108">在 自訂控制項中定義資源<xref:System.Windows.ResourceDictionary>會影響效能，該控制項的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca896-108">Defining resources in a custom control's <xref:System.Windows.ResourceDictionary> imposes a performance impact for every instance of that control.</span></span> <span data-ttu-id="ca896-109">比方說，如果您有需要大量效能的筆刷作業定義為屬於自訂控制項的資源定義和自訂控制項的許多執行個體，則應用程式的工作集將會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="ca896-109">For example, if you have performance-intensive brush operations defined as part of the resource definition of a custom control and many instances of the custom control, the application's working set will increase significantly.</span></span>  
  
 <span data-ttu-id="ca896-110">為了說明這點，請考慮下列項目。</span><span class="sxs-lookup"><span data-stu-id="ca896-110">To illustrate this point, consider the following.</span></span> <span data-ttu-id="ca896-111">假設您正在開發卡遊戲使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ca896-111">Let's say you are developing a card game using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="ca896-112">大部分的撲克牌遊戲，您必須使用 52 不同臉部的 52 張紙牌。</span><span class="sxs-lookup"><span data-stu-id="ca896-112">For most card games, you need 52 cards with 52 different faces.</span></span> <span data-ttu-id="ca896-113">您決定實作卡片自訂控制項，您定義 （每個都代表卡 face） 的 52 筆刷卡自訂控制項的資源中。</span><span class="sxs-lookup"><span data-stu-id="ca896-113">You decide to implement a card custom control and you define 52 brushes (each representing a card face) in the resources of your card custom control.</span></span> <span data-ttu-id="ca896-114">主要的應用程式中您一開始會建立此卡的自訂控制項 52 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca896-114">In your main application, you initially create 52 instances of this card custom control.</span></span> <span data-ttu-id="ca896-115">卡片的自訂控制項的每個執行個體產生 52 個執行個體<xref:System.Windows.Media.Brush>物件，可讓您總共 52 \* 52<xref:System.Windows.Media.Brush>應用程式中的物件。</span><span class="sxs-lookup"><span data-stu-id="ca896-115">Each instance of the card custom control generates 52 instances of <xref:System.Windows.Media.Brush> objects, which gives you a total of 52 \* 52 <xref:System.Windows.Media.Brush> objects in your application.</span></span> <span data-ttu-id="ca896-116">藉由移動到卡片的自訂控制項資源不足的筆刷<xref:System.Windows.Application>或<xref:System.Windows.Window>物件層級，或定義它們預設佈景主題自訂控制項，因為您現在共用 52 筆刷，減少應用程式的工作集52 的卡片控制項的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca896-116">By moving the brushes out of the card custom control resources to the <xref:System.Windows.Application> or <xref:System.Windows.Window> object level, or defining them in the default theme for the custom control, you reduce the working set of the application, since you are now sharing the 52 brushes among 52 instances of the card control.</span></span>  
  
## <a name="sharing-a-brush-without-copying"></a><span data-ttu-id="ca896-117">未複製的情況下共用筆刷</span><span class="sxs-lookup"><span data-stu-id="ca896-117">Sharing a Brush without Copying</span></span>  
 <span data-ttu-id="ca896-118">如果您有多個使用相同的項目<xref:System.Windows.Media.Brush>物件，定義為資源的筆刷並參考它，而不是定義在內嵌的筆刷[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ca896-118">If you have multiple elements using the same <xref:System.Windows.Media.Brush> object, define the brush as a resource and reference it, rather than defining the brush inline in [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span> <span data-ttu-id="ca896-119">這個方法會建立一個執行個體，並重複使用，而定義中的筆刷內嵌[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]建立新的執行個體，每個項目。</span><span class="sxs-lookup"><span data-stu-id="ca896-119">This method will create one instance and reuse it, whereas defining brushes inline in [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] creates a new instance for each element.</span></span>  
  
 <span data-ttu-id="ca896-120">下列標記範例說明這一點：</span><span class="sxs-lookup"><span data-stu-id="ca896-120">The following markup sample illustrates this point:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a><span data-ttu-id="ca896-121">使用靜態資源，可能的話</span><span class="sxs-lookup"><span data-stu-id="ca896-121">Use Static Resources when Possible</span></span>  
 <span data-ttu-id="ca896-122">靜態資源會提供任何 XAML 內容屬性的值，藉由查閱已定義之資源的參考。</span><span class="sxs-lookup"><span data-stu-id="ca896-122">A static resource provides a value for any XAML property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="ca896-123">該資源查閱行為相當於編譯時期查閱。</span><span class="sxs-lookup"><span data-stu-id="ca896-123">Lookup behavior for that resource is analogous to compile-time lookup.</span></span>  
  
 <span data-ttu-id="ca896-124">相反地，動態資源，可能會將裝置建立初始的編譯期間的暫時運算式，並因此延後資源的查閱，直到實際需要以建構物件，而要求的資源值。</span><span class="sxs-lookup"><span data-stu-id="ca896-124">A dynamic resource, on the other hand, will create a temporary expression during the initial compilation and thus defer lookup for resources until the requested resource value is actually required in order to construct an object.</span></span> <span data-ttu-id="ca896-125">該資源查閱行為相當於執行階段對應，它會影響效能。</span><span class="sxs-lookup"><span data-stu-id="ca896-125">Lookup behavior for that resource is analogous to run-time lookup, which imposes a performance impact.</span></span> <span data-ttu-id="ca896-126">使用靜態資源，請盡可能使用動態資源，只在必要時在您的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ca896-126">Use static resources whenever possible in your application, using dynamic resources only when necessary.</span></span>  
  
 <span data-ttu-id="ca896-127">下列標記範例示範如何使用這兩種類型的資源：</span><span class="sxs-lookup"><span data-stu-id="ca896-127">The following markup sample shows the use of both types of resources:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a><span data-ttu-id="ca896-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca896-128">See also</span></span>
- [<span data-ttu-id="ca896-129">最佳化 WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="ca896-129">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="ca896-130">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="ca896-130">Planning for Application Performance</span></span>](planning-for-application-performance.md)
- [<span data-ttu-id="ca896-131">運用硬體</span><span class="sxs-lookup"><span data-stu-id="ca896-131">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)
- [<span data-ttu-id="ca896-132">版面配置與設計</span><span class="sxs-lookup"><span data-stu-id="ca896-132">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)
- [<span data-ttu-id="ca896-133">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="ca896-133">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="ca896-134">物件行為</span><span class="sxs-lookup"><span data-stu-id="ca896-134">Object Behavior</span></span>](optimizing-performance-object-behavior.md)
- [<span data-ttu-id="ca896-135">Text</span><span class="sxs-lookup"><span data-stu-id="ca896-135">Text</span></span>](optimizing-performance-text.md)
- [<span data-ttu-id="ca896-136">資料繫結</span><span class="sxs-lookup"><span data-stu-id="ca896-136">Data Binding</span></span>](optimizing-performance-data-binding.md)
- [<span data-ttu-id="ca896-137">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="ca896-137">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)
