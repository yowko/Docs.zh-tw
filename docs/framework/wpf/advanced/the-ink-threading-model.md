---
title: "筆墨執行緒模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application user interface thread [WPF]
- stylus plug-in
- ink threading model [WPF]
- ink [WPF], rendering
- pen thread [WPF]
- threading model [WPF]
- rendering ink [WPF]
- dynamic rendering thread [WPF]
- ink collection plug-in
- plug-ins [WPF], for ink
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8eb0cf9f1cbb1be688f228b7bbd10a3a3ca6ed0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="the-ink-threading-model"></a><span data-ttu-id="ec560-102">筆墨執行緒模型</span><span class="sxs-lookup"><span data-stu-id="ec560-102">The Ink Threading Model</span></span>
<span data-ttu-id="ec560-103">其中一個 Tablet PC 上的優點是筆墨的，它感覺更像是撰寫使用一般紙筆。</span><span class="sxs-lookup"><span data-stu-id="ec560-103">One of the benefits of ink on a Tablet PC is that it feels a lot like writing with a regular pen and paper.</span></span>  <span data-ttu-id="ec560-104">若要達成此目的，tablet 畫筆會收集輸入的資料，以更高的速率超過沒有滑鼠，而且會筆跡轉譯成使用者寫入。</span><span class="sxs-lookup"><span data-stu-id="ec560-104">To accomplish this, the tablet pen collects input data at a much higher rate than a mouse does and renders the ink as the user writes.</span></span>  <span data-ttu-id="ec560-105">應用程式的使用者介面 (UI) 執行緒不足，無法收集畫筆資料及呈現筆墨，因為它可能會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="ec560-105">The application's user interface (UI) thread is not sufficient for collecting pen data and rendering ink, because it can become blocked.</span></span>  <span data-ttu-id="ec560-106">若要解決此，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用者撰寫的筆墨時，應用程式會使用兩個額外的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ec560-106">To solve this, a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application uses two additional threads when a user writes ink.</span></span>  
  
 <span data-ttu-id="ec560-107">下列清單描述使用的收集和呈現數位筆跡執行緒：</span><span class="sxs-lookup"><span data-stu-id="ec560-107">The following list describes the threads that take part in collecting and rendering digital ink:</span></span>  
  
-   <span data-ttu-id="ec560-108">畫筆執行緒會將手寫筆的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ec560-108">Pen thread - the thread that takes input from the stylus.</span></span>  <span data-ttu-id="ec560-109">（事實上，這是在執行緒集區中，但本主題是指其畫筆執行緒）。</span><span class="sxs-lookup"><span data-stu-id="ec560-109">(In reality, this is a thread pool, but this topic refers to it as a pen thread.)</span></span>  
  
-   <span data-ttu-id="ec560-110">應用程式使用者介面執行緒控制應用程式的使用者介面執行緒。</span><span class="sxs-lookup"><span data-stu-id="ec560-110">Application user interface thread - the thread that controls the user interface of the application.</span></span>  
  
-   <span data-ttu-id="ec560-111">動態呈現執行緒： 呈現時使用者筆墨執行緒繪製筆觸。</span><span class="sxs-lookup"><span data-stu-id="ec560-111">Dynamic rendering thread - the thread that renders the ink while the user draws a stroke.</span></span> <span data-ttu-id="ec560-112">視窗 Presentation Foundation 中所述的動態呈現執行緒會呈現其他 UI 項目，應用程式執行緒以外的不同[執行緒模型](../../../../docs/framework/wpf/advanced/threading-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ec560-112">The dynamic rendering thread is different than the thread that renders other UI elements for the application, as mentioned in Window Presentation Foundation [Threading Model](../../../../docs/framework/wpf/advanced/threading-model.md).</span></span>  
  
 <span data-ttu-id="ec560-113">不論應用程式使用筆跡的模型都相同<xref:System.Windows.Controls.InkCanvas>或自訂控制項中的一個類似[建立筆跡輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ec560-113">The inking model is the same whether the application uses the <xref:System.Windows.Controls.InkCanvas> or a custom control similar to the one in [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  <span data-ttu-id="ec560-114">雖然本主題討論的執行緒<xref:System.Windows.Controls.InkCanvas>，相同的概念適用於當您建立自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="ec560-114">Although this topic discusses threading in terms of the <xref:System.Windows.Controls.InkCanvas>, the same concepts apply when you create a custom control.</span></span>  
  
## <a name="threading-overview"></a><span data-ttu-id="ec560-115">執行緒處理概觀</span><span class="sxs-lookup"><span data-stu-id="ec560-115">Threading Overview</span></span>  
 <span data-ttu-id="ec560-116">下圖說明的執行緒模型，當使用者繪製筆觸時：</span><span class="sxs-lookup"><span data-stu-id="ec560-116">The following diagram illustrates the threading model when a user draws a stroke:</span></span>  
  
 <span data-ttu-id="ec560-117">![繪製筆觸期間的執行緒模型。] (../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")</span><span class="sxs-lookup"><span data-stu-id="ec560-117">![Threading model while drawing a stroke.](../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")</span></span>  
  
1.  <span data-ttu-id="ec560-118">使用者繪製筆觸時發生的動作</span><span class="sxs-lookup"><span data-stu-id="ec560-118">Actions occurring while the user draws the stroke</span></span>  
  
    1.  <span data-ttu-id="ec560-119">當使用者繪製筆觸時，手寫筆的點有畫筆執行緒上。</span><span class="sxs-lookup"><span data-stu-id="ec560-119">When the user draws a stroke, the stylus points come in on the pen thread.</span></span>  <span data-ttu-id="ec560-120">手寫筆外掛程式，包括<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、 接受手寫筆上的點畫筆執行緒並有機會修改過他們的<xref:System.Windows.Controls.InkCanvas>接收它們。</span><span class="sxs-lookup"><span data-stu-id="ec560-120">Stylus plug-ins, including the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, accept the stylus points on the pen thread and have the chance to modify them before the <xref:System.Windows.Controls.InkCanvas> receives them.</span></span>  
  
    2.  <span data-ttu-id="ec560-121"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呈現手寫筆的點上的動態呈現執行緒。</span><span class="sxs-lookup"><span data-stu-id="ec560-121">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the stylus points on the dynamic rendering thread.</span></span> <span data-ttu-id="ec560-122">這會發生在上一個步驟相同的時間。</span><span class="sxs-lookup"><span data-stu-id="ec560-122">This happens at the same time as the previous step.</span></span>  
  
    3.  <span data-ttu-id="ec560-123"><xref:System.Windows.Controls.InkCanvas>接收手寫筆在 UI 執行緒上的點。</span><span class="sxs-lookup"><span data-stu-id="ec560-123">The <xref:System.Windows.Controls.InkCanvas> receives the stylus points on the UI thread.</span></span>  
  
2.  <span data-ttu-id="ec560-124">發生使用者結束筆觸動作</span><span class="sxs-lookup"><span data-stu-id="ec560-124">Actions occurring after the user ends the stroke</span></span>  
  
    1.  <span data-ttu-id="ec560-125">當使用者完成繪製筆觸<xref:System.Windows.Controls.InkCanvas>建立<xref:System.Windows.Ink.Stroke>物件，並將它加入至<xref:System.Windows.Controls.InkPresenter>，它以靜態方式呈現。</span><span class="sxs-lookup"><span data-stu-id="ec560-125">When the user finishes drawing the stroke, the <xref:System.Windows.Controls.InkCanvas> creates a <xref:System.Windows.Ink.Stroke> object and adds it to the <xref:System.Windows.Controls.InkPresenter>, which statically renders it.</span></span>  
  
    2.  <span data-ttu-id="ec560-126">UI 執行緒警示<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>筆觸以靜態方式轉譯，所以<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>筆劃其視覺表示法中移除。</span><span class="sxs-lookup"><span data-stu-id="ec560-126">The UI thread alerts the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> that the stroke is statically rendered, so the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> removes its visual representation of the stroke.</span></span>  
  
## <a name="ink-collection-and-stylus-plug-ins"></a><span data-ttu-id="ec560-127">集合筆跡和手寫筆外掛程式</span><span class="sxs-lookup"><span data-stu-id="ec560-127">Ink collection and Stylus Plug-ins</span></span>  
 <span data-ttu-id="ec560-128">每個<xref:System.Windows.UIElement>具有<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。</span><span class="sxs-lookup"><span data-stu-id="ec560-128">Each <xref:System.Windows.UIElement> has a <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span>  <span data-ttu-id="ec560-129"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中的物件<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>接收且可修改手寫筆上的點畫筆執行緒。</span><span class="sxs-lookup"><span data-stu-id="ec560-129">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> receive and can modify the stylus points on the pen thread.</span></span> <span data-ttu-id="ec560-130"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>物件接收的順序根據手寫筆的點<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。</span><span class="sxs-lookup"><span data-stu-id="ec560-130">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects receive the stylus points according to their order in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span>  
  
 <span data-ttu-id="ec560-131">下列圖表說明在假設性的情況下其中<xref:System.Windows.UIElement.StylusPlugIns%2A>集合<xref:System.Windows.UIElement>包含`stylusPlugin1`、 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，和`stylusPlugin2`，依此順序。</span><span class="sxs-lookup"><span data-stu-id="ec560-131">The following diagram illustrates the hypothetical situation where the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection of a <xref:System.Windows.UIElement> contains `stylusPlugin1`, a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, and `stylusPlugin2`, in that order.</span></span>  
  
 <span data-ttu-id="ec560-132">![Stylusplugin 效果順序會影響輸出。] (../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")</span><span class="sxs-lookup"><span data-stu-id="ec560-132">![Order of Stylus Plugins affect output.](../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")</span></span>  
  
 <span data-ttu-id="ec560-133">在上圖中，會發生下列行為：</span><span class="sxs-lookup"><span data-stu-id="ec560-133">In the previous diagram, the following behavior takes place:</span></span>  
  
1.  <span data-ttu-id="ec560-134">`StylusPlugin1`修改的值，x 和 y。</span><span class="sxs-lookup"><span data-stu-id="ec560-134">`StylusPlugin1` modifies the values for x and y.</span></span>  
  
2.  <span data-ttu-id="ec560-135"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收已修改的手寫筆的點，並呈現它們的動態呈現執行緒上。</span><span class="sxs-lookup"><span data-stu-id="ec560-135"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives the modified stylus points and renders them on the dynamic rendering thread.</span></span>  
  
3.  <span data-ttu-id="ec560-136">`StylusPlugin2`接收已修改的手寫筆的點，並進一步修改的 x 值和 y。</span><span class="sxs-lookup"><span data-stu-id="ec560-136">`StylusPlugin2` receives the modified stylus points and further modifies the values for x and y.</span></span>  
  
4.  <span data-ttu-id="ec560-137">應用程式收集手寫筆的點，並當使用者完成筆劃，以靜態方式呈現筆觸。</span><span class="sxs-lookup"><span data-stu-id="ec560-137">The application collects the stylus points, and, when the user finishes the stroke, statically renders the stroke.</span></span>  
  
 <span data-ttu-id="ec560-138">假設`stylusPlugin1`將手寫筆的點限制為矩形和`stylusPlugin2`轉譯手寫筆右邊的點。</span><span class="sxs-lookup"><span data-stu-id="ec560-138">Suppose that `stylusPlugin1` restricts the stylus points to a rectangle and `stylusPlugin2` translates the stylus points to the right.</span></span>  <span data-ttu-id="ec560-139">在前述案例中，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收受限制的手寫筆的點，但未翻譯的手寫筆的點。</span><span class="sxs-lookup"><span data-stu-id="ec560-139">In the previous scenario, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives the restricted stylus points, but not the translated stylus points.</span></span>  <span data-ttu-id="ec560-140">當使用者繪製筆觸時，筆劃轉譯矩形界限內，但看起來轉譯直到使用者取消畫筆筆觸。</span><span class="sxs-lookup"><span data-stu-id="ec560-140">When the user draws the stroke, the stroke is rendered within the bounds of the rectangle, but the stroke doesn't appear to be translated until the user lifts the pen.</span></span>  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a><span data-ttu-id="ec560-141">使用手寫筆外掛程式在 UI 執行緒上執行作業</span><span class="sxs-lookup"><span data-stu-id="ec560-141">Performing operations with a Stylus Plug-in on the UI thread</span></span>  
 <span data-ttu-id="ec560-142">無法在畫筆的執行緒上執行精確的點擊測試，因為某些項目可能有時會接收其他項目的手寫筆輸入。</span><span class="sxs-lookup"><span data-stu-id="ec560-142">Because accurate hit-testing cannot be performed on the pen thread, some elements might occasionally receive stylus input intended for other elements.</span></span> <span data-ttu-id="ec560-143">如果您需要確定輸入執行作業之前已正確傳遞，訂閱，並執行中的作業<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>， <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>，或<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="ec560-143">If you need to make sure the input was routed correctly before performing an operation, subscribe to and perform the operation in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, or <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> method.</span></span> <span data-ttu-id="ec560-144">執行精確的點擊測試之後，這些方法會叫用由應用程式執行緒。</span><span class="sxs-lookup"><span data-stu-id="ec560-144">These methods are invoked by the application thread after accurate hit-testing has been performed.</span></span> <span data-ttu-id="ec560-145">若要訂閱這些方法，請呼叫<xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A>發生於畫筆執行緒的方法中的方法。</span><span class="sxs-lookup"><span data-stu-id="ec560-145">To subscribe to these methods, call the <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> method in the method that occurs on the pen thread.</span></span>  
  
 <span data-ttu-id="ec560-146">下圖說明畫筆執行緒與 UI 執行緒，相對於的手寫筆事件之間的關聯性<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>。</span><span class="sxs-lookup"><span data-stu-id="ec560-146">The following diagram illustrates the relationship between the pen thread and UI thread with respect to the stylus events of a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.</span></span>  
  
 <span data-ttu-id="ec560-147">![筆跡執行緒模型 &#40;UI 和 Pen &#41;] (../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")</span><span class="sxs-lookup"><span data-stu-id="ec560-147">![Ink Threading Models &#40;UI and Pen&#41;](../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")</span></span>  
  
## <a name="rendering-ink"></a><span data-ttu-id="ec560-148">呈現筆墨</span><span class="sxs-lookup"><span data-stu-id="ec560-148">Rendering Ink</span></span>  
 <span data-ttu-id="ec560-149">當使用者繪製筆觸，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>讓筆跡出現 「 資料流程 」 畫筆從 UI 執行緒忙碌，即使呈現不同的執行緒上的筆墨。</span><span class="sxs-lookup"><span data-stu-id="ec560-149">As the user draws a stroke, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the ink on a separate thread so the ink appears to "flow" from the pen even when the UI thread is busy.</span></span>  <span data-ttu-id="ec560-150"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>視覺化樹狀結構建置動態呈現執行緒上，因為它會收集手寫筆的點。</span><span class="sxs-lookup"><span data-stu-id="ec560-150">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> builds a visual tree on the dynamic rendering thread as it collects stylus points.</span></span>  <span data-ttu-id="ec560-151">當使用者完成筆劃<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>詢問應用程式會在下一步的轉譯階段會收到通知。</span><span class="sxs-lookup"><span data-stu-id="ec560-151">When the user finishes the stroke, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> asks to be notified when the application does the next rendering pass.</span></span>  <span data-ttu-id="ec560-152">應用程式完成下一步的呈現階段之後<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>清除其視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ec560-152">After the application completes the next rendering pass, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cleans up its visual tree.</span></span>  <span data-ttu-id="ec560-153">下圖說明此程序。</span><span class="sxs-lookup"><span data-stu-id="ec560-153">The following diagram illustrates this process.</span></span>  
  
 <span data-ttu-id="ec560-154">![筆跡執行緒圖表](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")</span><span class="sxs-lookup"><span data-stu-id="ec560-154">![Ink threading diagram](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")</span></span>  
  
1.  <span data-ttu-id="ec560-155">使用者開始筆觸。</span><span class="sxs-lookup"><span data-stu-id="ec560-155">The user begins the stroke.</span></span>  
  
    1.  <span data-ttu-id="ec560-156"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>建立的視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ec560-156">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> creates the visual tree.</span></span>  
  
2.  <span data-ttu-id="ec560-157">使用者繪製筆觸。</span><span class="sxs-lookup"><span data-stu-id="ec560-157">The user is drawing the stroke.</span></span>  
  
    1.  <span data-ttu-id="ec560-158"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>建置的視覺化樹狀。</span><span class="sxs-lookup"><span data-stu-id="ec560-158">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> builds the visual tree.</span></span>  
  
3.  <span data-ttu-id="ec560-159">在使用者結束筆觸。</span><span class="sxs-lookup"><span data-stu-id="ec560-159">The user ends the stroke.</span></span>  
  
    1.  <span data-ttu-id="ec560-160"><xref:System.Windows.Controls.InkPresenter>筆劃將其視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ec560-160">The <xref:System.Windows.Controls.InkPresenter> adds the stroke to its visual tree.</span></span>  
  
    2.  <span data-ttu-id="ec560-161">媒體整合層級 （軍事） 以靜態方式呈現筆劃。</span><span class="sxs-lookup"><span data-stu-id="ec560-161">The Media Integration Layer (MIL) statically renders the strokes.</span></span>  
  
    3.  <span data-ttu-id="ec560-162"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>清除視覺效果。</span><span class="sxs-lookup"><span data-stu-id="ec560-162">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cleans up the visuals.</span></span>
