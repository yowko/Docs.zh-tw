---
title: "自訂呈現筆墨"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 481990acdf2f5b8f798144d36434569b9e2cd481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-rendering-ink"></a><span data-ttu-id="91a52-102">自訂呈現筆墨</span><span class="sxs-lookup"><span data-stu-id="91a52-102">Custom Rendering Ink</span></span>
<span data-ttu-id="91a52-103"><xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>屬性為筆劃的端點可讓您指定的外觀為筆劃的端點，例如其大小、 色彩和形狀，但有時可能會想要自訂外觀以外的視野<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>允許。</span><span class="sxs-lookup"><span data-stu-id="91a52-103">The <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property of a stroke allows you to specify the appearance of a stroke, such as its size, color, and shape, but there may be times that you want to customize the appearance beyond what <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> allow.</span></span> <span data-ttu-id="91a52-104">您可能想要自訂筆跡外觀，轉譯具噴槍、油畫及許多其他效果的外觀。</span><span class="sxs-lookup"><span data-stu-id="91a52-104">You may want to customize the appearance of ink by rendering in the appearance of an air brush, oil paint, and many other effects.</span></span> <span data-ttu-id="91a52-105">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]可讓您自訂要實作自訂轉譯筆墨<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和<xref:System.Windows.Ink.Stroke>物件。</span><span class="sxs-lookup"><span data-stu-id="91a52-105">The [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] allows you to custom render ink by implementing a custom <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and <xref:System.Windows.Ink.Stroke> object.</span></span>  
  
 <span data-ttu-id="91a52-106">本主題包含下列子章節：</span><span class="sxs-lookup"><span data-stu-id="91a52-106">This topic contains the following subsections:</span></span>  
  
-   [<span data-ttu-id="91a52-107">架構</span><span class="sxs-lookup"><span data-stu-id="91a52-107">Architecture</span></span>](#Architecture)  
  
-   [<span data-ttu-id="91a52-108">實作動態轉譯器</span><span class="sxs-lookup"><span data-stu-id="91a52-108">Implementing a Dynamic Renderer</span></span>](#ImplementingADynamicRenderer)  
  
-   [<span data-ttu-id="91a52-109">實作自訂筆劃</span><span class="sxs-lookup"><span data-stu-id="91a52-109">Implementing Custom Strokes</span></span>](#ImplementingCustomStrokes)  
  
-   [<span data-ttu-id="91a52-110">實作自訂 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="91a52-110">Implementing a Custom InkCanvas</span></span>](#ImplementingACustomInkCanvas)  
  
-   [<span data-ttu-id="91a52-111">結論</span><span class="sxs-lookup"><span data-stu-id="91a52-111">Conclusion</span></span>](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a><span data-ttu-id="91a52-112">架構</span><span class="sxs-lookup"><span data-stu-id="91a52-112">Architecture</span></span>  
 <span data-ttu-id="91a52-113">當使用者在筆跡介面寫入筆跡，且在筆劃再次新增至啟用手寫功能的介面之後，筆跡轉譯出現兩次。</span><span class="sxs-lookup"><span data-stu-id="91a52-113">Ink rendering occurs two times; when a user writes ink to an inking surface, and again after the stroke is added to the ink-enabled surface.</span></span> <span data-ttu-id="91a52-114"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呈現筆墨，當使用者將 tablet 畫筆在數位板，而<xref:System.Windows.Ink.Stroke>加入的項目之後呈現其本身。</span><span class="sxs-lookup"><span data-stu-id="91a52-114">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the ink when the user moves the tablet pen on the digitizer, and the <xref:System.Windows.Ink.Stroke> renders itself once it is added to an element.</span></span>  
  
 <span data-ttu-id="91a52-115">動態轉譯筆跡時有三個類別要實作。</span><span class="sxs-lookup"><span data-stu-id="91a52-115">There are three classes to implement when dynamically rendering ink.</span></span>  
  
1.  <span data-ttu-id="91a52-116">**DynamicRenderer**： 實作的類別，衍生自<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。</span><span class="sxs-lookup"><span data-stu-id="91a52-116">**DynamicRenderer**: Implement a class that derives from <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="91a52-117">這個類別是特製化<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>它是繪製呈現筆觸。</span><span class="sxs-lookup"><span data-stu-id="91a52-117">This class is a specialized <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> that renders the stroke as it is drawn.</span></span> <span data-ttu-id="91a52-118"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>進行個別的執行緒上轉譯，讓筆跡介面出現收集筆墨，即使應用程式使用者介面 (UI) 執行緒會封鎖。</span><span class="sxs-lookup"><span data-stu-id="91a52-118">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> does the rendering on a separate thread, so the inking surface appears to collect ink even when the application user interface (UI) thread is blocked.</span></span> <span data-ttu-id="91a52-119">如需執行緒模型的詳細資訊，請參閱[筆跡執行緒模型](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)。</span><span class="sxs-lookup"><span data-stu-id="91a52-119">For more information about the threading model, see [The Ink Threading Model](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).</span></span> <span data-ttu-id="91a52-120">若要自訂以動態方式呈現筆觸，覆寫<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="91a52-120">To customize dynamically rendering a stroke, override the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> method.</span></span>  
  
2.  <span data-ttu-id="91a52-121">**筆觸**： 實作的類別，衍生自<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="91a52-121">**Stroke**: Implement a class that derives from <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="91a52-122">這個類別會負責的靜態轉譯<xref:System.Windows.Input.StylusPoint>資料轉換成之後<xref:System.Windows.Ink.Stroke>物件。</span><span class="sxs-lookup"><span data-stu-id="91a52-122">This class is responsible for static rendering of the <xref:System.Windows.Input.StylusPoint> data after it has been converted into a <xref:System.Windows.Ink.Stroke> object.</span></span> <span data-ttu-id="91a52-123">覆寫<xref:System.Windows.Ink.Stroke.DrawCore%2A>方法，以確保該靜態轉譯筆劃部分是一致的動態呈現。</span><span class="sxs-lookup"><span data-stu-id="91a52-123">Override the <xref:System.Windows.Ink.Stroke.DrawCore%2A> method to ensure that static rendering of the stroke is consistent with dynamic rendering.</span></span>  
  
3.  <span data-ttu-id="91a52-124">**InkCanvas:**實作的類別，衍生自<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="91a52-124">**InkCanvas:** Implement a class that derives from <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="91a52-125">指派自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="91a52-125">Assign the customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property.</span></span> <span data-ttu-id="91a52-126">覆寫<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>方法並加入至自訂筆觸<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="91a52-126">Override the <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> method and add a custom stroke to the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property.</span></span> <span data-ttu-id="91a52-127">這可確保筆跡外觀的一致。</span><span class="sxs-lookup"><span data-stu-id="91a52-127">This ensures that the appearance of the ink is consistent.</span></span>  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a><span data-ttu-id="91a52-128">實作動態轉譯器</span><span class="sxs-lookup"><span data-stu-id="91a52-128">Implementing a Dynamic Renderer</span></span>  
 <span data-ttu-id="91a52-129">雖然<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>類別是標準的一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、 執行多個特殊的轉譯，您必須建立自訂的動態轉譯器，衍生自<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>並覆寫<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="91a52-129">Although the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> class is a standard part of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], to perform more specialized rendering, you must create a customized dynamic renderer that derives from the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and override the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> method.</span></span>  
  
 <span data-ttu-id="91a52-130">下列範例會示範自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>繪製以線性漸層筆刷效果的筆墨。</span><span class="sxs-lookup"><span data-stu-id="91a52-130">The following example demonstrates a customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> that draws ink with a linear gradient brush effect.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a><span data-ttu-id="91a52-131">實作自訂筆劃</span><span class="sxs-lookup"><span data-stu-id="91a52-131">Implementing Custom Strokes</span></span>  
 <span data-ttu-id="91a52-132">實作衍生自 <xref:System.Windows.Ink.Stroke> 的類別。</span><span class="sxs-lookup"><span data-stu-id="91a52-132">Implement a class that derives from <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="91a52-133">這個類別會負責轉譯<xref:System.Windows.Input.StylusPoint>資料轉換成之後<xref:System.Windows.Ink.Stroke>物件。</span><span class="sxs-lookup"><span data-stu-id="91a52-133">This class is responsible for rendering <xref:System.Windows.Input.StylusPoint> data after it has been converted into a <xref:System.Windows.Ink.Stroke> object.</span></span> <span data-ttu-id="91a52-134">覆寫<xref:System.Windows.Ink.Stroke.DrawCore%2A>類別以進行實際的繪圖。</span><span class="sxs-lookup"><span data-stu-id="91a52-134">Override the <xref:System.Windows.Ink.Stroke.DrawCore%2A> class to do the actual drawing.</span></span>  
  
 <span data-ttu-id="91a52-135">筆觸類別也可以使用儲存自訂資料<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="91a52-135">Your Stroke class can also store custom data by using the <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> method.</span></span> <span data-ttu-id="91a52-136">保存此資料時會與筆劃資料一起儲存。</span><span class="sxs-lookup"><span data-stu-id="91a52-136">This data is stored with the stroke data when persisted.</span></span>  
  
 <span data-ttu-id="91a52-137"><xref:System.Windows.Ink.Stroke>類別也可以執行點擊測試。</span><span class="sxs-lookup"><span data-stu-id="91a52-137">The <xref:System.Windows.Ink.Stroke> class can also perform hit testing.</span></span> <span data-ttu-id="91a52-138">您也可以實作您自己的點擊測試演算法藉由覆寫<xref:System.Windows.Ink.Stroke.HitTest%2A>目前類別中的方法。</span><span class="sxs-lookup"><span data-stu-id="91a52-138">You can also implement your own hit testing algorithm by overriding the <xref:System.Windows.Ink.Stroke.HitTest%2A> method in the current class.</span></span>  
  
 <span data-ttu-id="91a52-139">下列 C# 程式碼會示範自訂<xref:System.Windows.Ink.Stroke>呈現類別<xref:System.Windows.Input.StylusPoint>資料當做 3d 筆觸。</span><span class="sxs-lookup"><span data-stu-id="91a52-139">The following C# code demonstrates a custom <xref:System.Windows.Ink.Stroke> class that renders <xref:System.Windows.Input.StylusPoint> data as a 3-D stroke.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a><span data-ttu-id="91a52-140">實作自訂 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="91a52-140">Implementing a Custom InkCanvas</span></span>  
 <span data-ttu-id="91a52-141">最簡單的方式使用您自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>筆觸是實作衍生自的類別和<xref:System.Windows.Controls.InkCanvas>，並使用這些類別。</span><span class="sxs-lookup"><span data-stu-id="91a52-141">The easiest way to use your customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and stroke is to implement a class that derives from <xref:System.Windows.Controls.InkCanvas> and uses these classes.</span></span> <span data-ttu-id="91a52-142"><xref:System.Windows.Controls.InkCanvas>具有<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性，指定當使用者繪製筆觸的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="91a52-142">The <xref:System.Windows.Controls.InkCanvas> has a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property that specifies how the stroke is rendered when the user is drawing it.</span></span>  
  
 <span data-ttu-id="91a52-143">若要自訂轉譯筆劃上<xref:System.Windows.Controls.InkCanvas>執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="91a52-143">To custom render strokes on an <xref:System.Windows.Controls.InkCanvas> do the following:</span></span>  
  
-   <span data-ttu-id="91a52-144">建立衍生自類別<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="91a52-144">Create a class that derives from the <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
-   <span data-ttu-id="91a52-145">指定您自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="91a52-145">Assign your customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="91a52-146">覆寫 <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="91a52-146">Override the <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> method.</span></span> <span data-ttu-id="91a52-147">在此方法中，移除已新增至 InkCanvas 的原始筆劃。</span><span class="sxs-lookup"><span data-stu-id="91a52-147">In this method, remove the original stroke that was added to the InkCanvas.</span></span> <span data-ttu-id="91a52-148">然後建立自訂筆觸、 將它加入<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性，並呼叫基底類別的新<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>，其中包含自訂筆觸。</span><span class="sxs-lookup"><span data-stu-id="91a52-148">Then create a custom stroke, add it to the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property, and call the base class with a new <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> that contains the custom stroke.</span></span>  
  
 <span data-ttu-id="91a52-149">下列 C# 程式碼會示範自訂<xref:System.Windows.Controls.InkCanvas>使用自訂類別<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>並收集自訂筆觸。</span><span class="sxs-lookup"><span data-stu-id="91a52-149">The following C# code demonstrates a custom <xref:System.Windows.Controls.InkCanvas> class that uses a customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and collects custom strokes.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <span data-ttu-id="91a52-150"><xref:System.Windows.Controls.InkCanvas>可以有一個以上<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。</span><span class="sxs-lookup"><span data-stu-id="91a52-150">An <xref:System.Windows.Controls.InkCanvas> can have more than one <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="91a52-151">您可以加入多個<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>物件加入至<xref:System.Windows.Controls.InkCanvas>藉由加入<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="91a52-151">You can add multiple <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objects to the <xref:System.Windows.Controls.InkCanvas> by adding them to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span>  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="91a52-152">結論</span><span class="sxs-lookup"><span data-stu-id="91a52-152">Conclusion</span></span>  
 <span data-ttu-id="91a52-153">您可以藉由衍生您自己自訂的筆墨外觀<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>， <xref:System.Windows.Ink.Stroke>，和<xref:System.Windows.Controls.InkCanvas>類別。</span><span class="sxs-lookup"><span data-stu-id="91a52-153">You can customize the appearance of ink by deriving your own <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, and <xref:System.Windows.Controls.InkCanvas> classes.</span></span> <span data-ttu-id="91a52-154">當使用者繪製並收集筆劃後，這些類別可合力確保筆劃外觀的一致。</span><span class="sxs-lookup"><span data-stu-id="91a52-154">Together, these classes ensure that the appearance of the stroke is consistent when the user draws the stroke and after it is collected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a52-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="91a52-155">See Also</span></span>  
 [<span data-ttu-id="91a52-156">筆跡進階處理</span><span class="sxs-lookup"><span data-stu-id="91a52-156">Advanced Ink Handling</span></span>](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
