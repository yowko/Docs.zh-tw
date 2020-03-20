---
title: 攔截手寫筆的輸入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 17cf42a9d6d94d6ea12399561af5647df3b4d8c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181923"
---
# <a name="intercepting-input-from-the-stylus"></a><span data-ttu-id="88b88-102">攔截手寫筆的輸入</span><span class="sxs-lookup"><span data-stu-id="88b88-102">Intercepting Input from the Stylus</span></span>
<span data-ttu-id="88b88-103">該<xref:System.Windows.Input.StylusPlugIns>體系結構為實現對<xref:System.Windows.Input.Stylus>輸入的低級控制和創建數位筆跡<xref:System.Windows.Ink.Stroke>物件提供了一種機制。</span><span class="sxs-lookup"><span data-stu-id="88b88-103">The <xref:System.Windows.Input.StylusPlugIns> architecture provides a mechanism for implementing low-level control over <xref:System.Windows.Input.Stylus> input and the creation of digital ink <xref:System.Windows.Ink.Stroke> objects.</span></span> <span data-ttu-id="88b88-104">該<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類提供了一種機制，用於實現自訂行為並將其應用於來自手寫筆設備的資料流程，以實現最佳性能。</span><span class="sxs-lookup"><span data-stu-id="88b88-104">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> class provides a mechanism for you to implement custom behavior and apply it to the stream of data coming from the stylus device for the optimal performance.</span></span>  
  
 <span data-ttu-id="88b88-105">本主題包含下列子章節：</span><span class="sxs-lookup"><span data-stu-id="88b88-105">This topic contains the following subsections:</span></span>  
  
- [<span data-ttu-id="88b88-106">建築</span><span class="sxs-lookup"><span data-stu-id="88b88-106">Architecture</span></span>](#Architecture)  
  
- [<span data-ttu-id="88b88-107">實現手寫外掛程式</span><span class="sxs-lookup"><span data-stu-id="88b88-107">Implementing Stylus Plug-ins</span></span>](#ImplementingStylusPlugins)  
  
- [<span data-ttu-id="88b88-108">將外掛程式添加到 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="88b88-108">Adding Your Plug-in to an InkCanvas</span></span>](#AddingYourPluginToAnInkCanvas)  
  
- [<span data-ttu-id="88b88-109">結論</span><span class="sxs-lookup"><span data-stu-id="88b88-109">Conclusion</span></span>](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a><span data-ttu-id="88b88-110">架構</span><span class="sxs-lookup"><span data-stu-id="88b88-110">Architecture</span></span>  
 <span data-ttu-id="88b88-111">是<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>[手寫輸入](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90))API 的演變，在[訪問和操作筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))中描述。</span><span class="sxs-lookup"><span data-stu-id="88b88-111">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> is the evolution of the [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) APIs, described in [Accessing and Manipulating Pen Input](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="88b88-112">每個<xref:System.Windows.UIElement>都有一<xref:System.Windows.UIElement.StylusPlugIns%2A>個屬性是<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。</span><span class="sxs-lookup"><span data-stu-id="88b88-112">Each <xref:System.Windows.UIElement> has a <xref:System.Windows.UIElement.StylusPlugIns%2A> property that is a <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span> <span data-ttu-id="88b88-113">您可以將 添加到<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>元素的屬性<xref:System.Windows.UIElement.StylusPlugIns%2A>以在生成資料時操作<xref:System.Windows.Input.StylusPoint>資料。</span><span class="sxs-lookup"><span data-stu-id="88b88-113">You can add a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> to an element's <xref:System.Windows.UIElement.StylusPlugIns%2A> property to manipulate <xref:System.Windows.Input.StylusPoint> data as it is generated.</span></span> <span data-ttu-id="88b88-114"><xref:System.Windows.Input.StylusPoint>資料由系統數位化器支援的所有屬性組成，包括<xref:System.Windows.Input.StylusPoint.X%2A>和<xref:System.Windows.Input.StylusPoint.Y%2A>點資料以及<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>資料。</span><span class="sxs-lookup"><span data-stu-id="88b88-114"><xref:System.Windows.Input.StylusPoint> data consists of all the properties supported by the system digitizer, including the <xref:System.Windows.Input.StylusPoint.X%2A> and <xref:System.Windows.Input.StylusPoint.Y%2A> point data, as well as <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> data.</span></span>  
  
 <span data-ttu-id="88b88-115">將<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的物件直接插入到設備<xref:System.Windows.Input.Stylus>的資料流程中，當您將 添加到<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>屬性時。 <xref:System.Windows.UIElement.StylusPlugIns%2A></span><span class="sxs-lookup"><span data-stu-id="88b88-115">Your <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects are inserted directly into the stream of data coming from the <xref:System.Windows.Input.Stylus> device when you add the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span> <span data-ttu-id="88b88-116">外掛程式添加到<xref:System.Windows.UIElement.StylusPlugIns%2A>集合的順序決定了它們接收<xref:System.Windows.Input.StylusPoint>資料的順序。</span><span class="sxs-lookup"><span data-stu-id="88b88-116">The order in which plug-ins are added to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection dictates the order in which they will receive <xref:System.Windows.Input.StylusPoint> data.</span></span> <span data-ttu-id="88b88-117">例如，如果添加篩選器外掛程式，將輸入限制到特定區域，然後添加一個外掛程式，在編寫手勢時識別手勢，則識別手勢的外掛程式將收到篩選<xref:System.Windows.Input.StylusPoint>的資料。</span><span class="sxs-lookup"><span data-stu-id="88b88-117">For example, if you add a filter plug-in that restricts input to a particular region, and then add a plug-in that recognizes gestures as they are written, the plug-in that recognizes gestures will receive filtered <xref:System.Windows.Input.StylusPoint> data.</span></span>  
  
<a name="ImplementingStylusPlugins"></a>
## <a name="implementing-stylus-plug-ins"></a><span data-ttu-id="88b88-118">實現手寫外掛程式</span><span class="sxs-lookup"><span data-stu-id="88b88-118">Implementing Stylus Plug-ins</span></span>  
 <span data-ttu-id="88b88-119">要實現外掛程式，請從<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>派生類。</span><span class="sxs-lookup"><span data-stu-id="88b88-119">To implement a plug-in, derive a class from <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.</span></span> <span data-ttu-id="88b88-120">類應用 o 資料流程，因為它來自 。 <xref:System.Windows.Input.Stylus></span><span class="sxs-lookup"><span data-stu-id="88b88-120">This class is applied o the stream of data as it comes in from the <xref:System.Windows.Input.Stylus>.</span></span> <span data-ttu-id="88b88-121">在此類中，您可以修改<xref:System.Windows.Input.StylusPoint>資料的值。</span><span class="sxs-lookup"><span data-stu-id="88b88-121">In this class you can modify the values of the <xref:System.Windows.Input.StylusPoint> data.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="88b88-122">如果<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>引發或導致異常，應用程式將關閉。</span><span class="sxs-lookup"><span data-stu-id="88b88-122">If a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> throws or causes an exception, the application will close.</span></span> <span data-ttu-id="88b88-123">應徹底測試使用 和<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>僅在您確定 不會引發異常時才使用控制項<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的控制項。</span><span class="sxs-lookup"><span data-stu-id="88b88-123">You should thoroughly test controls that consume a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and only use a control if you are certain the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> will not throw an exception.</span></span>  
  
 <span data-ttu-id="88b88-124">下面的示例演示了一個外掛程式，該<xref:System.Windows.Input.StylusPoint.X%2A>外掛程式通過修改<xref:System.Windows.Input.StylusPoint.Y%2A><xref:System.Windows.Input.StylusPoint>資料中的 和 值來限制手寫筆輸入。<xref:System.Windows.Input.Stylus>因為資料來自設備。</span><span class="sxs-lookup"><span data-stu-id="88b88-124">The following example demonstrates a plug-in that restricts the stylus input by modifying the <xref:System.Windows.Input.StylusPoint.X%2A> and <xref:System.Windows.Input.StylusPoint.Y%2A> values in the <xref:System.Windows.Input.StylusPoint> data as it comes in from the <xref:System.Windows.Input.Stylus> device.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>
## <a name="adding-your-plug-in-to-an-inkcanvas"></a><span data-ttu-id="88b88-125">將外掛程式添加到 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="88b88-125">Adding Your Plug-in to an InkCanvas</span></span>  
 <span data-ttu-id="88b88-126">使用自訂外掛程式的最簡單方法是實現從 InkCanvas 派生的類並將其添加到<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="88b88-126">The easiest way to use your custom plug-in is to implement a class that derives from InkCanvas and add it to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span>  
  
 <span data-ttu-id="88b88-127">下面的示例演示了篩選墨<xref:System.Windows.Controls.InkCanvas>跡的自訂。</span><span class="sxs-lookup"><span data-stu-id="88b88-127">The following example demonstrates a custom <xref:System.Windows.Controls.InkCanvas> that filters the ink.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 <span data-ttu-id="88b88-128">如果向應用程式添加`FilterInkCanvas`並運行它，您會注意到，在使用者完成筆劃之前，墨蹟不會局限于區域。</span><span class="sxs-lookup"><span data-stu-id="88b88-128">If you add a `FilterInkCanvas` to your application and run it, you will notice that the ink isn't restricted to a region until after the user completes a stroke.</span></span> <span data-ttu-id="88b88-129">這是因為<xref:System.Windows.Controls.InkCanvas>具有 屬性<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>，該屬性是<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，並且已經是<xref:System.Windows.UIElement.StylusPlugIns%2A>集合的成員。</span><span class="sxs-lookup"><span data-stu-id="88b88-129">This is because the <xref:System.Windows.Controls.InkCanvas> has a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property, which is a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and is already a member of the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection.</span></span> <span data-ttu-id="88b88-130">添加到集合<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中的<xref:System.Windows.UIElement.StylusPlugIns%2A>自訂在接收資料後<xref:System.Windows.Input.StylusPoint><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收資料。</span><span class="sxs-lookup"><span data-stu-id="88b88-130">The custom <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> you added to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection receives the <xref:System.Windows.Input.StylusPoint> data after <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives data.</span></span> <span data-ttu-id="88b88-131">因此，<xref:System.Windows.Input.StylusPoint>在使用者抬起筆以結束筆劃之前，資料才會被篩選。</span><span class="sxs-lookup"><span data-stu-id="88b88-131">As a result, the <xref:System.Windows.Input.StylusPoint> data will not be filtered until after the user lifts the pen to end a stroke.</span></span> <span data-ttu-id="88b88-132">若要在使用者繪製墨蹟時篩選墨蹟，必須在 之前`FilterPlugin`<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>插入 。</span><span class="sxs-lookup"><span data-stu-id="88b88-132">To filter the ink as the user draws it, you must insert the `FilterPlugin` before the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span>  
  
 <span data-ttu-id="88b88-133">以下 C# 代碼演示了<xref:System.Windows.Controls.InkCanvas>在繪製墨蹟時篩選墨蹟的自訂。</span><span class="sxs-lookup"><span data-stu-id="88b88-133">The following C# code demonstrates a custom <xref:System.Windows.Controls.InkCanvas> that filters the ink as it is drawn.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a><span data-ttu-id="88b88-134">結論</span><span class="sxs-lookup"><span data-stu-id="88b88-134">Conclusion</span></span>  
 <span data-ttu-id="88b88-135">通過派生自己的<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類並將其插入到集合中<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，可以極大地增強數位筆跡的行為。</span><span class="sxs-lookup"><span data-stu-id="88b88-135">By deriving your own <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes and inserting them into <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> collections, you can greatly enhance the behavior of your digital ink.</span></span> <span data-ttu-id="88b88-136">您可以在生成<xref:System.Windows.Input.StylusPoint>資料時訪問資料，從而有機會自訂<xref:System.Windows.Input.Stylus>輸入。</span><span class="sxs-lookup"><span data-stu-id="88b88-136">You have access to the <xref:System.Windows.Input.StylusPoint> data as it is generated, giving you the opportunity to customize the <xref:System.Windows.Input.Stylus> input.</span></span> <span data-ttu-id="88b88-137">由於您對<xref:System.Windows.Input.StylusPoint>資料具有如此低級別的訪問，因此可以實現墨蹟收集和呈現，從而為您的應用程式提供最佳性能。</span><span class="sxs-lookup"><span data-stu-id="88b88-137">Because you have such low-level access to the <xref:System.Windows.Input.StylusPoint> data, you can implement ink collection and rendering with optimal performance for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88b88-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88b88-138">See also</span></span>

- [<span data-ttu-id="88b88-139">筆墨進階處理</span><span class="sxs-lookup"><span data-stu-id="88b88-139">Advanced Ink Handling</span></span>](advanced-ink-handling.md)
- <span data-ttu-id="88b88-140">[訪問和操作筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="88b88-140">[Accessing and Manipulating Pen Input](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))</span></span>
