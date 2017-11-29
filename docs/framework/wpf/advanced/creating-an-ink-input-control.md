---
title: "建立筆墨輸入控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cfc6553fe9dd176d2aa557df906141c13a5f425
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-an-ink-input-control"></a><span data-ttu-id="c1ae2-102">建立筆墨輸入控制項</span><span class="sxs-lookup"><span data-stu-id="c1ae2-102">Creating an Ink Input Control</span></span>
<span data-ttu-id="c1ae2-103">您可以建立的自訂控制項，動態及靜態呈現筆墨。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-103">You can create a custom control that dynamically and statically renders ink.</span></span> <span data-ttu-id="c1ae2-104">這就是，轉譯為使用者繪製筆觸，導致出現 「 資料流程 」 從 tablet 畫筆，並後顯示筆墨會加入至控制項，透過 tablet 畫筆，從剪貼簿 貼上或從檔案載入的筆墨的筆墨。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-104">That is, render ink as a user draws a stroke, causing the ink to appear to "flow" from the tablet pen, and display ink after it is added to the control, either via the tablet pen, pasted from the Clipboard, or loaded from a file.</span></span> <span data-ttu-id="c1ae2-105">若要以動態方式呈現筆墨，必須使用您的控制項<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-105">To dynamically render ink, your control must use a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="c1ae2-106">若要以靜態方式轉譯筆墨，您必須覆寫手寫筆事件方法 (<xref:System.Windows.UIElement.OnStylusDown%2A>， <xref:System.Windows.UIElement.OnStylusMove%2A>，和<xref:System.Windows.UIElement.OnStylusUp%2A>) 來收集<xref:System.Windows.Input.StylusPoint>資料，建立筆觸，並將其新增<xref:System.Windows.Controls.InkPresenter>（呈現在控制項上的筆墨）。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-106">To statically render ink, you must override the stylus event methods (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, and <xref:System.Windows.UIElement.OnStylusUp%2A>) to collect <xref:System.Windows.Input.StylusPoint> data, create strokes, and add them to an <xref:System.Windows.Controls.InkPresenter> (which renders the ink on the control).</span></span>  
  
 <span data-ttu-id="c1ae2-107">本主題包含下列子章節：</span><span class="sxs-lookup"><span data-stu-id="c1ae2-107">This topic contains the following subsections:</span></span>  
  
-   [<span data-ttu-id="c1ae2-108">如何： 收集手寫筆點資料，並建立筆墨筆劃</span><span class="sxs-lookup"><span data-stu-id="c1ae2-108">How to: Collect Stylus Point Data and Create Ink Strokes</span></span>](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [<span data-ttu-id="c1ae2-109">如何： 啟用您的控制項為接受來自滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="c1ae2-109">How to: Enable Your Control to Accept Input from the Mouse</span></span>](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [<span data-ttu-id="c1ae2-110">將它放在一起</span><span class="sxs-lookup"><span data-stu-id="c1ae2-110">Putting it together</span></span>](#PuttingItTogether)  
  
-   [<span data-ttu-id="c1ae2-111">使用額外的外掛程式和 DynamicRenderers</span><span class="sxs-lookup"><span data-stu-id="c1ae2-111">Using Additional Plug-ins and DynamicRenderers</span></span>](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [<span data-ttu-id="c1ae2-112">結論</span><span class="sxs-lookup"><span data-stu-id="c1ae2-112">Conclusion</span></span>](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a><span data-ttu-id="c1ae2-113">如何： 收集手寫筆點資料，並建立筆墨筆劃</span><span class="sxs-lookup"><span data-stu-id="c1ae2-113">How to: Collect Stylus Point Data and Create Ink Strokes</span></span>  
 <span data-ttu-id="c1ae2-114">若要建立控制項，收集和管理筆墨筆劃執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c1ae2-114">To create a control that collects and manages ink strokes do the following:</span></span>  
  
1.  <span data-ttu-id="c1ae2-115">自<xref:System.Windows.Controls.Control>或其中一個類別衍生自<xref:System.Windows.Controls.Control>，例如<xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-115">Derive a class from <xref:System.Windows.Controls.Control> or one of the classes derived from <xref:System.Windows.Controls.Control>, such as <xref:System.Windows.Controls.Label>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  <span data-ttu-id="c1ae2-116">新增<xref:System.Windows.Controls.InkPresenter>至類別，並將<xref:System.Windows.Controls.ContentControl.Content%2A>屬性至新<xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-116">Add an <xref:System.Windows.Controls.InkPresenter> to the class and set the <xref:System.Windows.Controls.ContentControl.Content%2A> property to the new <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  <span data-ttu-id="c1ae2-117">附加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>的<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至<xref:System.Windows.Controls.InkPresenter>藉由呼叫<xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>方法，並加入<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>至<xref:System.Windows.UIElement.StylusPlugIns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-117">Attach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkPresenter> by calling the <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> method, and add the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection.</span></span> <span data-ttu-id="c1ae2-118">這可讓<xref:System.Windows.Controls.InkPresenter>顯示筆墨手寫筆點資料會收集您的控制項。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-118">This allows the <xref:System.Windows.Controls.InkPresenter> to display the ink as the stylus point data is collected by your control.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  <span data-ttu-id="c1ae2-119">覆寫 <xref:System.Windows.UIElement.OnStylusDown%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-119">Override the <xref:System.Windows.UIElement.OnStylusDown%2A> method.</span></span>  <span data-ttu-id="c1ae2-120">在這種方法，擷取手寫筆呼叫<xref:System.Windows.Input.Stylus.Capture%2A>。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-120">In this method, capture the stylus with a call to <xref:System.Windows.Input.Stylus.Capture%2A>.</span></span> <span data-ttu-id="c1ae2-121">擷取手寫筆，您的控制項將會繼續接收<xref:System.Windows.UIElement.StylusMove>和<xref:System.Windows.UIElement.StylusUp>事件即使手寫筆離開控制項的界限。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-121">By capturing the stylus, your control will to continue to receive <xref:System.Windows.UIElement.StylusMove> and <xref:System.Windows.UIElement.StylusUp> events even if the stylus leaves the control's boundaries.</span></span> <span data-ttu-id="c1ae2-122">這不是絕對必要，但可以很好的使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-122">This is not strictly mandatory, but almost always desired for a good user experience.</span></span> <span data-ttu-id="c1ae2-123">建立新<xref:System.Windows.Input.StylusPointCollection>收集<xref:System.Windows.Input.StylusPoint>資料。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-123">Create a new <xref:System.Windows.Input.StylusPointCollection> to gather <xref:System.Windows.Input.StylusPoint> data.</span></span> <span data-ttu-id="c1ae2-124">最後，會加入一組初始的<xref:System.Windows.Input.StylusPoint>資料<xref:System.Windows.Input.StylusPointCollection>。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-124">Finally, add the initial set of <xref:System.Windows.Input.StylusPoint> data to the <xref:System.Windows.Input.StylusPointCollection>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  <span data-ttu-id="c1ae2-125">覆寫<xref:System.Windows.UIElement.OnStylusMove%2A>方法並加入<xref:System.Windows.Input.StylusPoint>資料<xref:System.Windows.Input.StylusPointCollection>您稍早建立的物件。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-125">Override the <xref:System.Windows.UIElement.OnStylusMove%2A> method and add the <xref:System.Windows.Input.StylusPoint> data to the <xref:System.Windows.Input.StylusPointCollection> object that you created earlier.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  <span data-ttu-id="c1ae2-126">覆寫<xref:System.Windows.UIElement.OnStylusUp%2A>方法並建立新<xref:System.Windows.Ink.Stroke>與<xref:System.Windows.Input.StylusPointCollection>資料。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-126">Override the <xref:System.Windows.UIElement.OnStylusUp%2A> method and create a new <xref:System.Windows.Ink.Stroke> with the <xref:System.Windows.Input.StylusPointCollection> data.</span></span> <span data-ttu-id="c1ae2-127">加入新<xref:System.Windows.Ink.Stroke>您建立以<xref:System.Windows.Controls.InkPresenter.Strokes%2A>集合<xref:System.Windows.Controls.InkPresenter>放開手寫筆擷取。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-127">Add the new <xref:System.Windows.Ink.Stroke> you created to the <xref:System.Windows.Controls.InkPresenter.Strokes%2A> collection of the <xref:System.Windows.Controls.InkPresenter> and release stylus capture.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a><span data-ttu-id="c1ae2-128">如何： 啟用您的控制項為接受來自滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="c1ae2-128">How to: Enable Your Control to Accept Input from the Mouse</span></span>  
 <span data-ttu-id="c1ae2-129">如果將上述的控制項加入至您的應用程式，請執行時，使用滑鼠，做為輸入裝置，您會發現的筆劃不會保存。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-129">If you add the preceding control to your application, run it, and use the mouse as an input device, you will notice that the strokes are not persisted.</span></span> <span data-ttu-id="c1ae2-130">保存筆劃滑鼠做的輸入裝置時執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c1ae2-130">To persist the strokes when the mouse is used as the input device do the following:</span></span>  
  
1.  <span data-ttu-id="c1ae2-131">覆寫<xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A>並建立新<xref:System.Windows.Input.StylusPointCollection>發生事件時取得的滑鼠位置，並建立<xref:System.Windows.Input.StylusPoint>使用點資料，然後新增<xref:System.Windows.Input.StylusPoint>至<xref:System.Windows.Input.StylusPointCollection>。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-131">Override the <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> and create a new <xref:System.Windows.Input.StylusPointCollection> Get the position of the mouse when the event occurred and create a <xref:System.Windows.Input.StylusPoint> using the point data and add the <xref:System.Windows.Input.StylusPoint> to the <xref:System.Windows.Input.StylusPointCollection>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  <span data-ttu-id="c1ae2-132">覆寫 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-132">Override the <xref:System.Windows.UIElement.OnMouseMove%2A> method.</span></span> <span data-ttu-id="c1ae2-133">取得滑鼠位置的事件發生時，並建立<xref:System.Windows.Input.StylusPoint>使用點資料。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-133">Get the position of the mouse when the event occurred and create a <xref:System.Windows.Input.StylusPoint> using the point data.</span></span>  <span data-ttu-id="c1ae2-134">新增<xref:System.Windows.Input.StylusPoint>至<xref:System.Windows.Input.StylusPointCollection>您稍早建立的物件。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-134">Add the <xref:System.Windows.Input.StylusPoint> to the <xref:System.Windows.Input.StylusPointCollection> object that you created earlier.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  <span data-ttu-id="c1ae2-135">覆寫 <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-135">Override the <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> method.</span></span>  <span data-ttu-id="c1ae2-136">建立新<xref:System.Windows.Ink.Stroke>與<xref:System.Windows.Input.StylusPointCollection>資料，並加入新<xref:System.Windows.Ink.Stroke>您建立以<xref:System.Windows.Controls.InkPresenter.Strokes%2A>集合<xref:System.Windows.Controls.InkPresenter>。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-136">Create a new <xref:System.Windows.Ink.Stroke> with the <xref:System.Windows.Input.StylusPointCollection> data, and add the new <xref:System.Windows.Ink.Stroke> you created to the <xref:System.Windows.Controls.InkPresenter.Strokes%2A> collection of the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a><span data-ttu-id="c1ae2-137">將它放在一起</span><span class="sxs-lookup"><span data-stu-id="c1ae2-137">Putting it together</span></span>  
 <span data-ttu-id="c1ae2-138">下列範例是當使用者使用滑鼠或畫筆收集筆墨的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-138">The following example is a custom control that collects ink when the user uses either the mouse or the pen.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a><span data-ttu-id="c1ae2-139">使用額外的外掛程式和 DynamicRenderers</span><span class="sxs-lookup"><span data-stu-id="c1ae2-139">Using Additional Plug-ins and DynamicRenderers</span></span>  
 <span data-ttu-id="c1ae2-140">InkCanvas，例如您的自訂控制項可以有自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>和其他<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>物件。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-140">Like the InkCanvas, your custom control can have custom <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and additional <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objects.</span></span> <span data-ttu-id="c1ae2-141">將這些新增到<xref:System.Windows.UIElement.StylusPlugIns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-141">Add these to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection.</span></span> <span data-ttu-id="c1ae2-142">順序<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中的物件<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>呈現時，會影響的筆墨外觀。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-142">The order of the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> affects the appearance of the ink when it is rendered.</span></span> <span data-ttu-id="c1ae2-143">假設您有<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呼叫`dynamicRenderer`和自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>呼叫`translatePlugin`，位移的 tablet 畫筆筆墨。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-143">Suppose you have a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> called `dynamicRenderer` and a custom <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> called `translatePlugin` that offsets the ink from the tablet pen.</span></span> <span data-ttu-id="c1ae2-144">如果`translatePlugin`是第一個<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，和`dynamicRenderer`是第二個，當使用者移動畫筆將位移 「 流 」 的筆墨。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-144">If `translatePlugin` is the first <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, and `dynamicRenderer` is the second, the ink that "flows" will be offset as the user moves the pen.</span></span> <span data-ttu-id="c1ae2-145">如果`dynamicRenderer`這是第一次，並`translatePlugin`是第二，直到使用者取消畫筆筆墨將位移。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-145">If `dynamicRenderer` is first, and `translatePlugin` is second, the ink will not be offset until the user lifts the pen.</span></span>  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="c1ae2-146">結論</span><span class="sxs-lookup"><span data-stu-id="c1ae2-146">Conclusion</span></span>  
 <span data-ttu-id="c1ae2-147">您可以建立會收集並呈現筆墨藉由覆寫手寫筆事件方法的控制項。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-147">You can create a control that collects and renders ink by overriding the stylus event methods.</span></span> <span data-ttu-id="c1ae2-148">藉由建立您自己的控制項，衍生您自己<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別，並將它們插入到<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，您可以實作幾乎任何想像數位筆跡與行為。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-148">By creating your own control, deriving your own <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes, and inserting them the into <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, you can implement virtually any behavior imaginable with digital ink.</span></span> <span data-ttu-id="c1ae2-149">您可以存取<xref:System.Windows.Input.StylusPoint>產生做為它的資料，讓您有機會自訂<xref:System.Windows.Input.Stylus>輸入，並轉譯為適合您的應用程式畫面上。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-149">You have access to the <xref:System.Windows.Input.StylusPoint> data as it is generated, giving you the opportunity to  customize <xref:System.Windows.Input.Stylus> input and render it on the screen as appropriate for your application.</span></span> <span data-ttu-id="c1ae2-150">因為這類低層級存取<xref:System.Windows.Input.StylusPoint>資料，您可以實作筆墨收集及呈現它以獲得最佳效能，您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c1ae2-150">Because you have such low-level access to the <xref:System.Windows.Input.StylusPoint> data, you can implement ink collection and render it with optimal performance for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ae2-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1ae2-151">See Also</span></span>  
 [<span data-ttu-id="c1ae2-152">筆跡進階處理</span><span class="sxs-lookup"><span data-stu-id="c1ae2-152">Advanced Ink Handling</span></span>](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [<span data-ttu-id="c1ae2-153">存取和管理畫筆輸入</span><span class="sxs-lookup"><span data-stu-id="c1ae2-153">Accessing and Manipulating Pen Input</span></span>](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
