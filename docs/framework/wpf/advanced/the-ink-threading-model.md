---
title: 筆墨執行緒模型
ms.date: 03/30/2017
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
ms.openlocfilehash: 8089c857d2406f8cfb357ba2efe188ad84605541
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377021"
---
# <a name="the-ink-threading-model"></a><span data-ttu-id="2973d-102">筆墨執行緒模型</span><span class="sxs-lookup"><span data-stu-id="2973d-102">The Ink Threading Model</span></span>
<span data-ttu-id="2973d-103">Tablet PC 上的好處之一是筆墨的，覺得有許多撰寫使用一般紙筆。</span><span class="sxs-lookup"><span data-stu-id="2973d-103">One of the benefits of ink on a Tablet PC is that it feels a lot like writing with a regular pen and paper.</span></span>  <span data-ttu-id="2973d-104">若要這麼做，tablet 畫筆會收集在更高的速率比滑鼠，並為使用者寫入會轉譯筆跡輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="2973d-104">To accomplish this, the tablet pen collects input data at a much higher rate than a mouse does and renders the ink as the user writes.</span></span>  <span data-ttu-id="2973d-105">應用程式的使用者介面 (UI) 執行緒不足，無法用來收集畫筆資料和呈現筆墨，因為它可能會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="2973d-105">The application's user interface (UI) thread is not sufficient for collecting pen data and rendering ink, because it can become blocked.</span></span>  <span data-ttu-id="2973d-106">若要解決，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]時使用者寫入筆跡，應用程式會使用兩個額外的執行緒。</span><span class="sxs-lookup"><span data-stu-id="2973d-106">To solve this, a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application uses two additional threads when a user writes ink.</span></span>  
  
 <span data-ttu-id="2973d-107">下列清單描述參與收集和呈現數位筆跡執行緒：</span><span class="sxs-lookup"><span data-stu-id="2973d-107">The following list describes the threads that take part in collecting and rendering digital ink:</span></span>  
  
-   <span data-ttu-id="2973d-108">畫筆執行緒的執行緒，會將手寫筆的輸入。</span><span class="sxs-lookup"><span data-stu-id="2973d-108">Pen thread - the thread that takes input from the stylus.</span></span>  <span data-ttu-id="2973d-109">（事實上，這是執行緒集區，但本主題會將它稱為畫筆執行緒）。</span><span class="sxs-lookup"><span data-stu-id="2973d-109">(In reality, this is a thread pool, but this topic refers to it as a pen thread.)</span></span>  
  
-   <span data-ttu-id="2973d-110">應用程式使用者介面執行緒控制的應用程式的使用者介面執行緒。</span><span class="sxs-lookup"><span data-stu-id="2973d-110">Application user interface thread - the thread that controls the user interface of the application.</span></span>  
  
-   <span data-ttu-id="2973d-111">動態呈現執行緒-之執行緒的轉譯筆跡時使用者繪製筆劃。</span><span class="sxs-lookup"><span data-stu-id="2973d-111">Dynamic rendering thread - the thread that renders the ink while the user draws a stroke.</span></span> <span data-ttu-id="2973d-112">動態呈現執行緒會呈現其他 UI 項目，應用程式執行緒以外的不同視窗 Presentation Foundation 中所述[執行緒模型](threading-model.md)。</span><span class="sxs-lookup"><span data-stu-id="2973d-112">The dynamic rendering thread is different than the thread that renders other UI elements for the application, as mentioned in Window Presentation Foundation [Threading Model](threading-model.md).</span></span>  
  
 <span data-ttu-id="2973d-113">筆跡的模型是相同的應用程式使用是否<xref:System.Windows.Controls.InkCanvas>或自訂控制項中的一個類似[建立筆墨輸入控制項](creating-an-ink-input-control.md)。</span><span class="sxs-lookup"><span data-stu-id="2973d-113">The inking model is the same whether the application uses the <xref:System.Windows.Controls.InkCanvas> or a custom control similar to the one in [Creating an Ink Input Control](creating-an-ink-input-control.md).</span></span>  <span data-ttu-id="2973d-114">雖然本主題討論執行緒的形式<xref:System.Windows.Controls.InkCanvas>，當您建立自訂控制項時，適用相同的概念。</span><span class="sxs-lookup"><span data-stu-id="2973d-114">Although this topic discusses threading in terms of the <xref:System.Windows.Controls.InkCanvas>, the same concepts apply when you create a custom control.</span></span>  
  
## <a name="threading-overview"></a><span data-ttu-id="2973d-115">執行緒處理概觀</span><span class="sxs-lookup"><span data-stu-id="2973d-115">Threading Overview</span></span>  
 <span data-ttu-id="2973d-116">下圖說明執行緒模型，當使用者繪製筆劃時：</span><span class="sxs-lookup"><span data-stu-id="2973d-116">The following diagram illustrates the threading model when a user draws a stroke:</span></span>  
  
 <span data-ttu-id="2973d-117">![繪製筆觸期間的執行緒模型。](./media/inkthreading-drawingink.png "InkThreading_DrawingInk")</span><span class="sxs-lookup"><span data-stu-id="2973d-117">![Threading model while drawing a stroke.](./media/inkthreading-drawingink.png "InkThreading_DrawingInk")</span></span>  
  
1.  <span data-ttu-id="2973d-118">發生使用者繪製筆劃時的動作</span><span class="sxs-lookup"><span data-stu-id="2973d-118">Actions occurring while the user draws the stroke</span></span>  
  
    1.  <span data-ttu-id="2973d-119">當使用者繪製筆劃時，手寫筆點有畫筆執行緒上。</span><span class="sxs-lookup"><span data-stu-id="2973d-119">When the user draws a stroke, the stylus points come in on the pen thread.</span></span>  <span data-ttu-id="2973d-120">手寫筆外掛程式，包括<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，接受畫筆執行緒上的手寫筆點，並有機會修改它們之前<xref:System.Windows.Controls.InkCanvas>接收它們。</span><span class="sxs-lookup"><span data-stu-id="2973d-120">Stylus plug-ins, including the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, accept the stylus points on the pen thread and have the chance to modify them before the <xref:System.Windows.Controls.InkCanvas> receives them.</span></span>  
  
    2.  <span data-ttu-id="2973d-121"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>呈現的動態呈現執行緒上的手寫筆點。</span><span class="sxs-lookup"><span data-stu-id="2973d-121">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the stylus points on the dynamic rendering thread.</span></span> <span data-ttu-id="2973d-122">這會發生於與上一個步驟相同的時間。</span><span class="sxs-lookup"><span data-stu-id="2973d-122">This happens at the same time as the previous step.</span></span>  
  
    3.  <span data-ttu-id="2973d-123"><xref:System.Windows.Controls.InkCanvas>接收在 UI 執行緒上的手寫筆點。</span><span class="sxs-lookup"><span data-stu-id="2973d-123">The <xref:System.Windows.Controls.InkCanvas> receives the stylus points on the UI thread.</span></span>  
  
2.  <span data-ttu-id="2973d-124">使用者結束筆劃後發生的動作</span><span class="sxs-lookup"><span data-stu-id="2973d-124">Actions occurring after the user ends the stroke</span></span>  
  
    1.  <span data-ttu-id="2973d-125">當使用者完成繪製的筆劃<xref:System.Windows.Controls.InkCanvas>會建立<xref:System.Windows.Ink.Stroke>物件，並將它加入至<xref:System.Windows.Controls.InkPresenter>，會以靜態方式呈現。</span><span class="sxs-lookup"><span data-stu-id="2973d-125">When the user finishes drawing the stroke, the <xref:System.Windows.Controls.InkCanvas> creates a <xref:System.Windows.Ink.Stroke> object and adds it to the <xref:System.Windows.Controls.InkPresenter>, which statically renders it.</span></span>  
  
    2.  <span data-ttu-id="2973d-126">UI 執行緒警示<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>靜態轉譯筆劃，因此<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>筆劃其視覺表示法中移除。</span><span class="sxs-lookup"><span data-stu-id="2973d-126">The UI thread alerts the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> that the stroke is statically rendered, so the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> removes its visual representation of the stroke.</span></span>  
  
## <a name="ink-collection-and-stylus-plug-ins"></a><span data-ttu-id="2973d-127">筆跡收集和手寫筆外掛程式</span><span class="sxs-lookup"><span data-stu-id="2973d-127">Ink collection and Stylus Plug-ins</span></span>  
 <span data-ttu-id="2973d-128">每個<xref:System.Windows.UIElement>具有<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。</span><span class="sxs-lookup"><span data-stu-id="2973d-128">Each <xref:System.Windows.UIElement> has a <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span>  <span data-ttu-id="2973d-129"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中的物件<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>接收，且可修改的畫筆執行緒上的手寫筆點。</span><span class="sxs-lookup"><span data-stu-id="2973d-129">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> receive and can modify the stylus points on the pen thread.</span></span> <span data-ttu-id="2973d-130"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>物件接收根據其順序中的手寫筆點<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。</span><span class="sxs-lookup"><span data-stu-id="2973d-130">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects receive the stylus points according to their order in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span>  
  
 <span data-ttu-id="2973d-131">下圖說明假設性情況其中<xref:System.Windows.UIElement.StylusPlugIns%2A>的集合<xref:System.Windows.UIElement>包含`stylusPlugin1`，則<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，和`stylusPlugin2`，依此順序。</span><span class="sxs-lookup"><span data-stu-id="2973d-131">The following diagram illustrates the hypothetical situation where the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection of a <xref:System.Windows.UIElement> contains `stylusPlugin1`, a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, and `stylusPlugin2`, in that order.</span></span>  
  
 <span data-ttu-id="2973d-132">![手寫筆外掛程式的順序會影響輸出。](./media/inkthreading-pluginorder.png "InkThreading_PluginOrder")</span><span class="sxs-lookup"><span data-stu-id="2973d-132">![Order of Stylus Plugins affect output.](./media/inkthreading-pluginorder.png "InkThreading_PluginOrder")</span></span>  
  
 <span data-ttu-id="2973d-133">在上圖中，會發生下列行為：</span><span class="sxs-lookup"><span data-stu-id="2973d-133">In the previous diagram, the following behavior takes place:</span></span>  
  
1.  <span data-ttu-id="2973d-134">`StylusPlugin1` 修改 x 值和 y。</span><span class="sxs-lookup"><span data-stu-id="2973d-134">`StylusPlugin1` modifies the values for x and y.</span></span>  
  
2.  <span data-ttu-id="2973d-135"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 接收已修改的手寫筆的點，並轉譯成動態呈現執行緒上。</span><span class="sxs-lookup"><span data-stu-id="2973d-135"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives the modified stylus points and renders them on the dynamic rendering thread.</span></span>  
  
3.  <span data-ttu-id="2973d-136">`StylusPlugin2` 接收已修改的手寫筆的點，並進一步修改 x 值和 y。</span><span class="sxs-lookup"><span data-stu-id="2973d-136">`StylusPlugin2` receives the modified stylus points and further modifies the values for x and y.</span></span>  
  
4.  <span data-ttu-id="2973d-137">應用程式會收集手寫筆的點，並當使用者完成筆劃，靜態轉譯筆劃。</span><span class="sxs-lookup"><span data-stu-id="2973d-137">The application collects the stylus points, and, when the user finishes the stroke, statically renders the stroke.</span></span>  
  
 <span data-ttu-id="2973d-138">假設`stylusPlugin1`限制的矩形的手寫筆的點和`stylusPlugin2`轉譯右邊的手寫筆點。</span><span class="sxs-lookup"><span data-stu-id="2973d-138">Suppose that `stylusPlugin1` restricts the stylus points to a rectangle and `stylusPlugin2` translates the stylus points to the right.</span></span>  <span data-ttu-id="2973d-139">在前一個案例中，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收限制的手寫筆的點，但未翻譯的手寫筆的點。</span><span class="sxs-lookup"><span data-stu-id="2973d-139">In the previous scenario, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives the restricted stylus points, but not the translated stylus points.</span></span>  <span data-ttu-id="2973d-140">當使用者繪製筆劃時，筆劃轉譯的矩形界限內，但筆劃不會出現轉譯，直到使用者拿起畫筆。</span><span class="sxs-lookup"><span data-stu-id="2973d-140">When the user draws the stroke, the stroke is rendered within the bounds of the rectangle, but the stroke doesn't appear to be translated until the user lifts the pen.</span></span>  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a><span data-ttu-id="2973d-141">使用手寫筆外掛程式在 UI 執行緒上執行作業</span><span class="sxs-lookup"><span data-stu-id="2973d-141">Performing operations with a Stylus Plug-in on the UI thread</span></span>  
 <span data-ttu-id="2973d-142">畫筆執行緒上無法執行精確的點擊測試，因為有些項目偶爾可能會收到其他項目的手寫筆輸入。</span><span class="sxs-lookup"><span data-stu-id="2973d-142">Because accurate hit-testing cannot be performed on the pen thread, some elements might occasionally receive stylus input intended for other elements.</span></span> <span data-ttu-id="2973d-143">如果您需要確定輸入執行作業之前已正確傳遞，訂閱，並執行中的作業<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>， <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>，或<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2973d-143">If you need to make sure the input was routed correctly before performing an operation, subscribe to and perform the operation in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, or <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> method.</span></span> <span data-ttu-id="2973d-144">執行精確的點擊測試之後，應用程式執行緒會叫用這些方法。</span><span class="sxs-lookup"><span data-stu-id="2973d-144">These methods are invoked by the application thread after accurate hit-testing has been performed.</span></span> <span data-ttu-id="2973d-145">若要訂閱這些方法，呼叫<xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A>發生於畫筆執行緒的方法中的方法。</span><span class="sxs-lookup"><span data-stu-id="2973d-145">To subscribe to these methods, call the <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> method in the method that occurs on the pen thread.</span></span>  
  
 <span data-ttu-id="2973d-146">下圖說明畫筆執行緒與 UI 執行緒相關的手寫筆事件之間的關係<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>。</span><span class="sxs-lookup"><span data-stu-id="2973d-146">The following diagram illustrates the relationship between the pen thread and UI thread with respect to the stylus events of a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.</span></span>  
  
 <span data-ttu-id="2973d-147">![筆墨執行緒模型&#40;UI 和 Pen&#41;](./media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")</span><span class="sxs-lookup"><span data-stu-id="2973d-147">![Ink Threading Models &#40;UI and Pen&#41;](./media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")</span></span>  
  
## <a name="rendering-ink"></a><span data-ttu-id="2973d-148">呈現筆墨</span><span class="sxs-lookup"><span data-stu-id="2973d-148">Rendering Ink</span></span>  
 <span data-ttu-id="2973d-149">當使用者繪製筆劃，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>會轉譯在個別執行緒上的筆墨，因此 「 順著 」 從畫筆甚至是在 UI 執行緒忙碌時顯示的筆墨。</span><span class="sxs-lookup"><span data-stu-id="2973d-149">As the user draws a stroke, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the ink on a separate thread so the ink appears to "flow" from the pen even when the UI thread is busy.</span></span>  <span data-ttu-id="2973d-150"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>動態呈現執行緒上建置視覺化樹狀結構，因為它會收集手寫筆點。</span><span class="sxs-lookup"><span data-stu-id="2973d-150">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> builds a visual tree on the dynamic rendering thread as it collects stylus points.</span></span>  <span data-ttu-id="2973d-151">當使用者完成筆劃，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>會要求應用程式會在下一步 的轉譯階段時收到通知。</span><span class="sxs-lookup"><span data-stu-id="2973d-151">When the user finishes the stroke, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> asks to be notified when the application does the next rendering pass.</span></span>  <span data-ttu-id="2973d-152">應用程式完成下一步 的呈現階段之後,<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>清除其視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2973d-152">After the application completes the next rendering pass, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cleans up its visual tree.</span></span>  <span data-ttu-id="2973d-153">下圖說明此程序。</span><span class="sxs-lookup"><span data-stu-id="2973d-153">The following diagram illustrates this process.</span></span>  
  
 <span data-ttu-id="2973d-154">![筆跡執行緒圖表](./media/inkthreading-visualtree.png "InkThreading_VisualTree")</span><span class="sxs-lookup"><span data-stu-id="2973d-154">![Ink threading diagram](./media/inkthreading-visualtree.png "InkThreading_VisualTree")</span></span>  
  
1.  <span data-ttu-id="2973d-155">使用者會開始筆劃。</span><span class="sxs-lookup"><span data-stu-id="2973d-155">The user begins the stroke.</span></span>  
  
    1.  <span data-ttu-id="2973d-156"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>建立視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2973d-156">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> creates the visual tree.</span></span>  
  
2.  <span data-ttu-id="2973d-157">使用者繪製筆劃。</span><span class="sxs-lookup"><span data-stu-id="2973d-157">The user is drawing the stroke.</span></span>  
  
    1.  <span data-ttu-id="2973d-158"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>建置視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2973d-158">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> builds the visual tree.</span></span>  
  
3.  <span data-ttu-id="2973d-159">筆劃端點使用者。</span><span class="sxs-lookup"><span data-stu-id="2973d-159">The user ends the stroke.</span></span>  
  
    1.  <span data-ttu-id="2973d-160"><xref:System.Windows.Controls.InkPresenter>將其視覺化樹狀結構中的筆劃。</span><span class="sxs-lookup"><span data-stu-id="2973d-160">The <xref:System.Windows.Controls.InkPresenter> adds the stroke to its visual tree.</span></span>  
  
    2.  <span data-ttu-id="2973d-161">媒體整合層 (.MIL) 靜態轉譯筆劃。</span><span class="sxs-lookup"><span data-stu-id="2973d-161">The Media Integration Layer (MIL) statically renders the strokes.</span></span>  
  
    3.  <span data-ttu-id="2973d-162"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>清除視覺效果。</span><span class="sxs-lookup"><span data-stu-id="2973d-162">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cleans up the visuals.</span></span>
