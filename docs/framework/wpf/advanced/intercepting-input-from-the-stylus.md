---
title: "攔截手寫筆的輸入"
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
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 611a2d2de56025e2f1b5add6106294834586f9af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="intercepting-input-from-the-stylus"></a><span data-ttu-id="b3a0f-102">攔截手寫筆的輸入</span><span class="sxs-lookup"><span data-stu-id="b3a0f-102">Intercepting Input from the Stylus</span></span>
<span data-ttu-id="b3a0f-103"><xref:System.Windows.Input.StylusPlugIns>架構提供一個機制，透過實作的低階控制<xref:System.Windows.Input.Stylus>輸入和建立數位筆跡<xref:System.Windows.Ink.Stroke>物件。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-103">The <xref:System.Windows.Input.StylusPlugIns> architecture provides a mechanism for implementing low-level control over <xref:System.Windows.Input.Stylus> input and the creation of digital ink <xref:System.Windows.Ink.Stroke> objects.</span></span> <span data-ttu-id="b3a0f-104"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別提供您實作自訂行為，並將它套用到來自手寫筆裝置以獲得最佳的效能資料的資料流的機制。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-104">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> class provides a mechanism for you to implement custom behavior and apply it to the stream of data coming from the stylus device for the optimal performance.</span></span>  
  
 <span data-ttu-id="b3a0f-105">本主題包含下列子章節：</span><span class="sxs-lookup"><span data-stu-id="b3a0f-105">This topic contains the following subsections:</span></span>  
  
-   [<span data-ttu-id="b3a0f-106">架構</span><span class="sxs-lookup"><span data-stu-id="b3a0f-106">Architecture</span></span>](#Architecture)  
  
-   [<span data-ttu-id="b3a0f-107">實作手寫筆外掛程式</span><span class="sxs-lookup"><span data-stu-id="b3a0f-107">Implementing Stylus Plug-ins</span></span>](#ImplementingStylusPlugins)  
  
-   [<span data-ttu-id="b3a0f-108">InkCanvas 加入外掛程式</span><span class="sxs-lookup"><span data-stu-id="b3a0f-108">Adding Your Plug-in to an InkCanvas</span></span>](#AddingYourPluginToAnInkCanvas)  
  
-   [<span data-ttu-id="b3a0f-109">結論</span><span class="sxs-lookup"><span data-stu-id="b3a0f-109">Conclusion</span></span>](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a><span data-ttu-id="b3a0f-110">架構</span><span class="sxs-lookup"><span data-stu-id="b3a0f-110">Architecture</span></span>  
 <span data-ttu-id="b3a0f-111"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>是的演進[StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409)所述的 Api[存取和操作畫筆輸入](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)，請在[Microsoft Windows XP Tablet PC Edition 軟體開發套件 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-111">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> is the evolution of the [StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) APIs, described in [Accessing and Manipulating Pen Input](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409), in the [Microsoft Windows XP Tablet PC Edition Software Development Kit 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).</span></span>  
  
 <span data-ttu-id="b3a0f-112">每個<xref:System.Windows.UIElement>具有<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-112">Each <xref:System.Windows.UIElement> has a <xref:System.Windows.UIElement.StylusPlugIns%2A> property that is a <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span> <span data-ttu-id="b3a0f-113">您可以加入<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的項目<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性來操作<xref:System.Windows.Input.StylusPoint>產生做為它的資料。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-113">You can add a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> to an element's <xref:System.Windows.UIElement.StylusPlugIns%2A> property to manipulate <xref:System.Windows.Input.StylusPoint> data as it is generated.</span></span> <span data-ttu-id="b3a0f-114"><xref:System.Windows.Input.StylusPoint>資料包含系統潀糔蠮，包括支援的所有屬性<xref:System.Windows.Input.StylusPoint.X%2A>和<xref:System.Windows.Input.StylusPoint.Y%2A>點的資料，以及<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>資料。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-114"><xref:System.Windows.Input.StylusPoint> data consists of all the properties supported by the system digitizer, including the <xref:System.Windows.Input.StylusPoint.X%2A> and <xref:System.Windows.Input.StylusPoint.Y%2A> point data, as well as <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> data.</span></span>  
  
 <span data-ttu-id="b3a0f-115">您<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>物件直接插入的資料來自資料流<xref:System.Windows.Input.Stylus>裝置，當您將加入<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>至<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-115">Your <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects are inserted directly into the stream of data coming from the <xref:System.Windows.Input.Stylus> device when you add the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span> <span data-ttu-id="b3a0f-116">在其中加入外掛程式順序<xref:System.Windows.UIElement.StylusPlugIns%2A>集合會要求他們將收到的順序<xref:System.Windows.Input.StylusPoint>資料。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-116">The order in which plug-ins are added to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection dictates the order in which they will receive <xref:System.Windows.Input.StylusPoint> data.</span></span> <span data-ttu-id="b3a0f-117">比方說，如果您加入篩選外掛程式，以限制到特定區域中，輸入，然後再新增 的寫法是可以辨識筆勢的外掛程式，外掛程式可辨識筆勢會收到篩選<xref:System.Windows.Input.StylusPoint>資料。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-117">For example, if you add a filter plug-in that restricts input to a particular region, and then add a plug-in that recognizes gestures as they are written, the plug-in that recognizes gestures will receive filtered <xref:System.Windows.Input.StylusPoint> data.</span></span>  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a><span data-ttu-id="b3a0f-118">實作手寫筆外掛程式</span><span class="sxs-lookup"><span data-stu-id="b3a0f-118">Implementing Stylus Plug-ins</span></span>  
 <span data-ttu-id="b3a0f-119">若要實作的外掛程式，衍生自<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-119">To implement a plug-in, derive a class from <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.</span></span> <span data-ttu-id="b3a0f-120">這個類別是套用的 o 中的資料流，因為它來自<xref:System.Windows.Input.Stylus>。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-120">This class is applied o the stream of data as it comes in from the <xref:System.Windows.Input.Stylus>.</span></span> <span data-ttu-id="b3a0f-121">此類別中，您可以修改的值<xref:System.Windows.Input.StylusPoint>資料。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-121">In this class you can modify the values of the <xref:System.Windows.Input.StylusPoint> data.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b3a0f-122">如果<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>擲回或造成例外狀況，應用程式即將關閉。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-122">If a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> throws or causes an exception, the application will close.</span></span> <span data-ttu-id="b3a0f-123">您應該徹底測試使用的控制項<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，並只使用控制，如果您確定<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-123">You should thoroughly test controls that consume a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and only use a control if you are certain the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> will not throw an exception.</span></span>  
  
 <span data-ttu-id="b3a0f-124">下列範例會示範外掛程式，藉由修改限制手寫筆輸入<xref:System.Windows.Input.StylusPoint.X%2A>和<xref:System.Windows.Input.StylusPoint.Y%2A>中的值<xref:System.Windows.Input.StylusPoint>資料，因為它來自<xref:System.Windows.Input.Stylus>裝置。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-124">The following example demonstrates a plug-in that restricts the stylus input by modifying the <xref:System.Windows.Input.StylusPoint.X%2A> and <xref:System.Windows.Input.StylusPoint.Y%2A> values in the <xref:System.Windows.Input.StylusPoint> data as it comes in from the <xref:System.Windows.Input.Stylus> device.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a><span data-ttu-id="b3a0f-125">InkCanvas 加入外掛程式</span><span class="sxs-lookup"><span data-stu-id="b3a0f-125">Adding Your Plug-in to an InkCanvas</span></span>  
 <span data-ttu-id="b3a0f-126">若要使用您的自訂外掛程式的最簡單方式是實作一個衍生自 InkCanvas 的類別，並將它加入<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-126">The easiest way to use your custom plug-in is to implement a class that derives from InkCanvas and add it to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span>  
  
 <span data-ttu-id="b3a0f-127">下列範例會示範自訂<xref:System.Windows.Controls.InkCanvas>篩選筆跡。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-127">The following example demonstrates a custom <xref:System.Windows.Controls.InkCanvas> that filters the ink.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 <span data-ttu-id="b3a0f-128">如果您將加入`FilterInkCanvas`應用程式和執行它，您會注意到筆墨筆劃使用者後不會限制為之前的區域。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-128">If you add a `FilterInkCanvas` to your application and run it, you will notice that the ink isn't restricted to a region until after the user completes a stroke.</span></span> <span data-ttu-id="b3a0f-129">這是因為<xref:System.Windows.Controls.InkCanvas>具有<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性，這是<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>且已隸屬<xref:System.Windows.UIElement.StylusPlugIns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-129">This is because the <xref:System.Windows.Controls.InkCanvas> has a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property, which is a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and is already a member of the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection.</span></span> <span data-ttu-id="b3a0f-130">自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>您已加入至<xref:System.Windows.UIElement.StylusPlugIns%2A>集合接收<xref:System.Windows.Input.StylusPoint>後的資料<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收資料。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-130">The custom <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> you added to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection receives the <xref:System.Windows.Input.StylusPoint> data after <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives data.</span></span> <span data-ttu-id="b3a0f-131">如此一來，<xref:System.Windows.Input.StylusPoint>資料將不會篩選直到之後使用者取消結束筆觸以畫筆。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-131">As a result, the <xref:System.Windows.Input.StylusPoint> data will not be filtered until after the user lifts the pen to end a stroke.</span></span> <span data-ttu-id="b3a0f-132">若要篩選使用者將它繪製的筆墨，您必須插入`FilterPlugin`之前<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-132">To filter the ink as the user draws it, you must insert the `FilterPlugin` before the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span>  
  
 <span data-ttu-id="b3a0f-133">下列 C# 程式碼會示範自訂<xref:System.Windows.Controls.InkCanvas>，篩選它是繪製的筆墨。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-133">The following C# code demonstrates a custom <xref:System.Windows.Controls.InkCanvas> that filters the ink as it is drawn.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="b3a0f-134">結論</span><span class="sxs-lookup"><span data-stu-id="b3a0f-134">Conclusion</span></span>  
 <span data-ttu-id="b3a0f-135">由衍生您自己<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別，並將其插入<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>集合，您可以大幅強化您的數位筆跡的行為。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-135">By deriving your own <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes and inserting them into <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> collections, you can greatly enhance the behavior of your digital ink.</span></span> <span data-ttu-id="b3a0f-136">您可以存取<xref:System.Windows.Input.StylusPoint>產生做為它的資料，讓您有機會自訂<xref:System.Windows.Input.Stylus>輸入。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-136">You have access to the <xref:System.Windows.Input.StylusPoint> data as it is generated, giving you the opportunity to customize the <xref:System.Windows.Input.Stylus> input.</span></span> <span data-ttu-id="b3a0f-137">因為這類低層級存取<xref:System.Windows.Input.StylusPoint>資料，您可以為您的應用程式實作筆墨收集和呈現以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="b3a0f-137">Because you have such low-level access to the <xref:System.Windows.Input.StylusPoint> data, you can implement ink collection and rendering with optimal performance for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a0f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3a0f-138">See Also</span></span>  
 [<span data-ttu-id="b3a0f-139">筆跡進階處理</span><span class="sxs-lookup"><span data-stu-id="b3a0f-139">Advanced Ink Handling</span></span>](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [<span data-ttu-id="b3a0f-140">存取和管理畫筆輸入</span><span class="sxs-lookup"><span data-stu-id="b3a0f-140">Accessing and Manipulating Pen Input</span></span>](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
