---
title: 建立筆墨輸入控制項
ms.date: 03/30/2017
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
ms.openlocfilehash: 394318488b0afb8e043389e0abc3f51dce8604c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186287"
---
# <a name="creating-an-ink-input-control"></a><span data-ttu-id="71f63-102">建立筆墨輸入控制項</span><span class="sxs-lookup"><span data-stu-id="71f63-102">Creating an Ink Input Control</span></span>
<span data-ttu-id="71f63-103">您可以創建動態和靜態渲染墨蹟的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="71f63-103">You can create a custom control that dynamically and statically renders ink.</span></span> <span data-ttu-id="71f63-104">也就是說，在使用者繪製筆劃時渲染墨蹟，導致墨蹟從 Tablet 筆中顯示為"流"，並在墨蹟添加到控制項後顯示墨蹟，通過 Tablet 筆、從剪貼簿粘貼或從檔載入。</span><span class="sxs-lookup"><span data-stu-id="71f63-104">That is, render ink as a user draws a stroke, causing the ink to appear to "flow" from the tablet pen, and display ink after it is added to the control, either via the tablet pen, pasted from the Clipboard, or loaded from a file.</span></span> <span data-ttu-id="71f63-105">要動態渲染墨蹟，控制項必須使用<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。</span><span class="sxs-lookup"><span data-stu-id="71f63-105">To dynamically render ink, your control must use a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="71f63-106">要靜態渲染墨蹟，必須重寫手寫筆事件方法<xref:System.Windows.UIElement.OnStylusDown%2A>（和<xref:System.Windows.UIElement.OnStylusMove%2A> <xref:System.Windows.UIElement.OnStylusUp%2A>） 以收集資料<xref:System.Windows.Input.StylusPoint>、創建描邊並將它們添加到 （<xref:System.Windows.Controls.InkPresenter>該方法在控制項上呈現墨蹟）。</span><span class="sxs-lookup"><span data-stu-id="71f63-106">To statically render ink, you must override the stylus event methods (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, and <xref:System.Windows.UIElement.OnStylusUp%2A>) to collect <xref:System.Windows.Input.StylusPoint> data, create strokes, and add them to an <xref:System.Windows.Controls.InkPresenter> (which renders the ink on the control).</span></span>  
  
 <span data-ttu-id="71f63-107">本主題包含下列子章節：</span><span class="sxs-lookup"><span data-stu-id="71f63-107">This topic contains the following subsections:</span></span>  
  
- [<span data-ttu-id="71f63-108">如何：收集手寫筆點資料並創建墨蹟描邊</span><span class="sxs-lookup"><span data-stu-id="71f63-108">How to: Collect Stylus Point Data and Create Ink Strokes</span></span>](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [<span data-ttu-id="71f63-109">如何：使控制項接受來自滑鼠的輸入</span><span class="sxs-lookup"><span data-stu-id="71f63-109">How to: Enable Your Control to Accept Input from the Mouse</span></span>](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [<span data-ttu-id="71f63-110">將它放在一起</span><span class="sxs-lookup"><span data-stu-id="71f63-110">Putting it together</span></span>](#PuttingItTogether)  
  
- [<span data-ttu-id="71f63-111">使用其他外掛程式和動態渲染器</span><span class="sxs-lookup"><span data-stu-id="71f63-111">Using Additional Plug-ins and DynamicRenderers</span></span>](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [<span data-ttu-id="71f63-112">結論</span><span class="sxs-lookup"><span data-stu-id="71f63-112">Conclusion</span></span>](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a><span data-ttu-id="71f63-113">如何：收集手寫筆點資料並創建墨蹟描邊</span><span class="sxs-lookup"><span data-stu-id="71f63-113">How to: Collect Stylus Point Data and Create Ink Strokes</span></span>  
 <span data-ttu-id="71f63-114">要創建收集和管理墨蹟描邊的控制項，請執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="71f63-114">To create a control that collects and manages ink strokes do the following:</span></span>  
  
1. <span data-ttu-id="71f63-115">派生來自<xref:System.Windows.Controls.Control>或 派生自<xref:System.Windows.Controls.Control>的類之一，<xref:System.Windows.Controls.Label>例如 。</span><span class="sxs-lookup"><span data-stu-id="71f63-115">Derive a class from <xref:System.Windows.Controls.Control> or one of the classes derived from <xref:System.Windows.Controls.Control>, such as <xref:System.Windows.Controls.Label>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. <span data-ttu-id="71f63-116">將<xref:System.Windows.Controls.InkPresenter>add 添加到 類<xref:System.Windows.Controls.ContentControl.Content%2A>並將 屬性設置為<xref:System.Windows.Controls.InkPresenter>新 。</span><span class="sxs-lookup"><span data-stu-id="71f63-116">Add an <xref:System.Windows.Controls.InkPresenter> to the class and set the <xref:System.Windows.Controls.ContentControl.Content%2A> property to the new <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. <span data-ttu-id="71f63-117"><xref:System.Windows.Controls.InkPresenter>通過調用<xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>方法將<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer><xref:System.Windows.UIElement.StylusPlugIns%2A><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>的 將 的<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>附加到 ，並將 添加到集合中。</span><span class="sxs-lookup"><span data-stu-id="71f63-117">Attach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkPresenter> by calling the <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> method, and add the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection.</span></span> <span data-ttu-id="71f63-118">這允許 在<xref:System.Windows.Controls.InkPresenter>控制項收集手寫筆點資料時顯示墨蹟。</span><span class="sxs-lookup"><span data-stu-id="71f63-118">This allows the <xref:System.Windows.Controls.InkPresenter> to display the ink as the stylus point data is collected by your control.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. <span data-ttu-id="71f63-119">覆寫 <xref:System.Windows.UIElement.OnStylusDown%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="71f63-119">Override the <xref:System.Windows.UIElement.OnStylusDown%2A> method.</span></span>  <span data-ttu-id="71f63-120">在此方法中，使用 調用<xref:System.Windows.Input.Stylus.Capture%2A>捕獲手寫筆。</span><span class="sxs-lookup"><span data-stu-id="71f63-120">In this method, capture the stylus with a call to <xref:System.Windows.Input.Stylus.Capture%2A>.</span></span> <span data-ttu-id="71f63-121">通過捕獲手寫筆，即使手寫筆離開控制項的邊界，您的控制項仍<xref:System.Windows.UIElement.StylusMove>將繼續<xref:System.Windows.UIElement.StylusUp>接收和事件。</span><span class="sxs-lookup"><span data-stu-id="71f63-121">By capturing the stylus, your control will to continue to receive <xref:System.Windows.UIElement.StylusMove> and <xref:System.Windows.UIElement.StylusUp> events even if the stylus leaves the control's boundaries.</span></span> <span data-ttu-id="71f63-122">這不是嚴格的強制性，但幾乎總是需要良好的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="71f63-122">This is not strictly mandatory, but almost always desired for a good user experience.</span></span> <span data-ttu-id="71f63-123">創建新資料<xref:System.Windows.Input.StylusPointCollection>以收集資料<xref:System.Windows.Input.StylusPoint>。</span><span class="sxs-lookup"><span data-stu-id="71f63-123">Create a new <xref:System.Windows.Input.StylusPointCollection> to gather <xref:System.Windows.Input.StylusPoint> data.</span></span> <span data-ttu-id="71f63-124">最後，將初始資料集<xref:System.Windows.Input.StylusPoint>添加到 。 <xref:System.Windows.Input.StylusPointCollection></span><span class="sxs-lookup"><span data-stu-id="71f63-124">Finally, add the initial set of <xref:System.Windows.Input.StylusPoint> data to the <xref:System.Windows.Input.StylusPointCollection>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. <span data-ttu-id="71f63-125">重寫<xref:System.Windows.UIElement.OnStylusMove%2A>方法並將<xref:System.Windows.Input.StylusPoint>資料添加到之前創建<xref:System.Windows.Input.StylusPointCollection>的物件。</span><span class="sxs-lookup"><span data-stu-id="71f63-125">Override the <xref:System.Windows.UIElement.OnStylusMove%2A> method and add the <xref:System.Windows.Input.StylusPoint> data to the <xref:System.Windows.Input.StylusPointCollection> object that you created earlier.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. <span data-ttu-id="71f63-126">重寫方法<xref:System.Windows.UIElement.OnStylusUp%2A>，使用<xref:System.Windows.Ink.Stroke><xref:System.Windows.Input.StylusPointCollection>資料創建新資料。</span><span class="sxs-lookup"><span data-stu-id="71f63-126">Override the <xref:System.Windows.UIElement.OnStylusUp%2A> method and create a new <xref:System.Windows.Ink.Stroke> with the <xref:System.Windows.Input.StylusPointCollection> data.</span></span> <span data-ttu-id="71f63-127">將您創建<xref:System.Windows.Ink.Stroke>的新樣式添加到<xref:System.Windows.Controls.InkPresenter.Strokes%2A><xref:System.Windows.Controls.InkPresenter>和 釋放手寫筆捕獲的集合中。</span><span class="sxs-lookup"><span data-stu-id="71f63-127">Add the new <xref:System.Windows.Ink.Stroke> you created to the <xref:System.Windows.Controls.InkPresenter.Strokes%2A> collection of the <xref:System.Windows.Controls.InkPresenter> and release stylus capture.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a><span data-ttu-id="71f63-128">如何：使控制項接受來自滑鼠的輸入</span><span class="sxs-lookup"><span data-stu-id="71f63-128">How to: Enable Your Control to Accept Input from the Mouse</span></span>  
 <span data-ttu-id="71f63-129">如果將前面的控制項添加到應用程式，運行它，並將滑鼠用作輸入裝置，您會注意到筆劃不會持久化。</span><span class="sxs-lookup"><span data-stu-id="71f63-129">If you add the preceding control to your application, run it, and use the mouse as an input device, you will notice that the strokes are not persisted.</span></span> <span data-ttu-id="71f63-130">要在將滑鼠用作輸入裝置時保留筆劃，請執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="71f63-130">To persist the strokes when the mouse is used as the input device do the following:</span></span>  
  
1. <span data-ttu-id="71f63-131">重寫<xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A>並創建新<xref:System.Windows.Input.StylusPointCollection>的"在事件發生時獲取滑鼠的位置"，並使用點資料創建<xref:System.Windows.Input.StylusPoint>一個 ，並將 添加到<xref:System.Windows.Input.StylusPoint>。 <xref:System.Windows.Input.StylusPointCollection></span><span class="sxs-lookup"><span data-stu-id="71f63-131">Override the <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> and create a new <xref:System.Windows.Input.StylusPointCollection> Get the position of the mouse when the event occurred and create a <xref:System.Windows.Input.StylusPoint> using the point data and add the <xref:System.Windows.Input.StylusPoint> to the <xref:System.Windows.Input.StylusPointCollection>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. <span data-ttu-id="71f63-132">覆寫 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="71f63-132">Override the <xref:System.Windows.UIElement.OnMouseMove%2A> method.</span></span> <span data-ttu-id="71f63-133">在事件發生時獲取滑鼠的位置，並使用點資料創建一個<xref:System.Windows.Input.StylusPoint>。</span><span class="sxs-lookup"><span data-stu-id="71f63-133">Get the position of the mouse when the event occurred and create a <xref:System.Windows.Input.StylusPoint> using the point data.</span></span>  <span data-ttu-id="71f63-134">將<xref:System.Windows.Input.StylusPoint>添加到之前<xref:System.Windows.Input.StylusPointCollection>創建的物件。</span><span class="sxs-lookup"><span data-stu-id="71f63-134">Add the <xref:System.Windows.Input.StylusPoint> to the <xref:System.Windows.Input.StylusPointCollection> object that you created earlier.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. <span data-ttu-id="71f63-135">覆寫 <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="71f63-135">Override the <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> method.</span></span>  <span data-ttu-id="71f63-136"><xref:System.Windows.Ink.Stroke>使用<xref:System.Windows.Input.StylusPointCollection>資料創建新資料，並將創建<xref:System.Windows.Ink.Stroke><xref:System.Windows.Controls.InkPresenter.Strokes%2A>的新添加到 集合中。 <xref:System.Windows.Controls.InkPresenter></span><span class="sxs-lookup"><span data-stu-id="71f63-136">Create a new <xref:System.Windows.Ink.Stroke> with the <xref:System.Windows.Input.StylusPointCollection> data, and add the new <xref:System.Windows.Ink.Stroke> you created to the <xref:System.Windows.Controls.InkPresenter.Strokes%2A> collection of the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>
## <a name="putting-it-together"></a><span data-ttu-id="71f63-137">將它放在一起</span><span class="sxs-lookup"><span data-stu-id="71f63-137">Putting it together</span></span>  
 <span data-ttu-id="71f63-138">下面的示例是一個自訂控制項，當使用者使用滑鼠或筆時收集墨蹟。</span><span class="sxs-lookup"><span data-stu-id="71f63-138">The following example is a custom control that collects ink when the user uses either the mouse or the pen.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a><span data-ttu-id="71f63-139">使用其他外掛程式和動態渲染器</span><span class="sxs-lookup"><span data-stu-id="71f63-139">Using Additional Plug-ins and DynamicRenderers</span></span>  
 <span data-ttu-id="71f63-140">與 InkCanvas 一樣，自訂控制項可以<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>具有自訂<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>物件和其他物件。</span><span class="sxs-lookup"><span data-stu-id="71f63-140">Like the InkCanvas, your custom control can have custom <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and additional <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objects.</span></span> <span data-ttu-id="71f63-141">將這些添加到集合中<xref:System.Windows.UIElement.StylusPlugIns%2A>。</span><span class="sxs-lookup"><span data-stu-id="71f63-141">Add these to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection.</span></span> <span data-ttu-id="71f63-142">中<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的物件的順序<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>會影響墨蹟在渲染時的外觀。</span><span class="sxs-lookup"><span data-stu-id="71f63-142">The order of the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> affects the appearance of the ink when it is rendered.</span></span> <span data-ttu-id="71f63-143">假設您有一個<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>已`dynamicRenderer`調用的自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>項`translatePlugin`，該調用的自訂項會偏移 Tablet 筆中的墨蹟。</span><span class="sxs-lookup"><span data-stu-id="71f63-143">Suppose you have a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> called `dynamicRenderer` and a custom <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> called `translatePlugin` that offsets the ink from the tablet pen.</span></span> <span data-ttu-id="71f63-144">如果`translatePlugin`是第一<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>個，<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>是第`dynamicRenderer`二個，則當使用者移動筆時，"流動"的墨蹟將被偏移。</span><span class="sxs-lookup"><span data-stu-id="71f63-144">If `translatePlugin` is the first <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, and `dynamicRenderer` is the second, the ink that "flows" will be offset as the user moves the pen.</span></span> <span data-ttu-id="71f63-145">如果`dynamicRenderer`是第一，是第`translatePlugin`二，則在使用者抬起筆之前，墨蹟不會偏移。</span><span class="sxs-lookup"><span data-stu-id="71f63-145">If `dynamicRenderer` is first, and `translatePlugin` is second, the ink will not be offset until the user lifts the pen.</span></span>  
  
<a name="AdvancedInkHandling_Conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="71f63-146">結論</span><span class="sxs-lookup"><span data-stu-id="71f63-146">Conclusion</span></span>  
 <span data-ttu-id="71f63-147">您可以創建通過重寫手寫筆事件方法收集和呈現墨蹟的控制項。</span><span class="sxs-lookup"><span data-stu-id="71f63-147">You can create a control that collects and renders ink by overriding the stylus event methods.</span></span> <span data-ttu-id="71f63-148">通過創建自己的控制項、派生自己的<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類並將它們插入 到 中<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，您可以實現幾乎任何使用數位筆跡可以想像到的行為。</span><span class="sxs-lookup"><span data-stu-id="71f63-148">By creating your own control, deriving your own <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes, and inserting them the into <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, you can implement virtually any behavior imaginable with digital ink.</span></span> <span data-ttu-id="71f63-149">您可以在生成<xref:System.Windows.Input.StylusPoint>資料時訪問資料，從而有機會自訂<xref:System.Windows.Input.Stylus>輸入並在螢幕上根據需要呈現它，以適合您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="71f63-149">You have access to the <xref:System.Windows.Input.StylusPoint> data as it is generated, giving you the opportunity to  customize <xref:System.Windows.Input.Stylus> input and render it on the screen as appropriate for your application.</span></span> <span data-ttu-id="71f63-150">由於您對<xref:System.Windows.Input.StylusPoint>資料具有如此低級別的訪問，因此可以實現墨蹟收集，並針對應用程式以最佳性能呈現它。</span><span class="sxs-lookup"><span data-stu-id="71f63-150">Because you have such low-level access to the <xref:System.Windows.Input.StylusPoint> data, you can implement ink collection and render it with optimal performance for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f63-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71f63-151">See also</span></span>

- [<span data-ttu-id="71f63-152">筆墨進階處理</span><span class="sxs-lookup"><span data-stu-id="71f63-152">Advanced Ink Handling</span></span>](advanced-ink-handling.md)
- <span data-ttu-id="71f63-153">[訪問和操作筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="71f63-153">[Accessing and Manipulating Pen Input](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))</span></span>
