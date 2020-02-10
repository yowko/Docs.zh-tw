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
ms.openlocfilehash: 7629843730a82584e94448ceac1ea574906876c9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095134"
---
# <a name="intercepting-input-from-the-stylus"></a><span data-ttu-id="298be-102">攔截手寫筆的輸入</span><span class="sxs-lookup"><span data-stu-id="298be-102">Intercepting Input from the Stylus</span></span>
<span data-ttu-id="298be-103"><xref:System.Windows.Input.StylusPlugIns> 架構提供一種機制，可對 <xref:System.Windows.Input.Stylus> 輸入和建立數位筆跡 <xref:System.Windows.Ink.Stroke> 物件進行低層級的控制。</span><span class="sxs-lookup"><span data-stu-id="298be-103">The <xref:System.Windows.Input.StylusPlugIns> architecture provides a mechanism for implementing low-level control over <xref:System.Windows.Input.Stylus> input and the creation of digital ink <xref:System.Windows.Ink.Stroke> objects.</span></span> <span data-ttu-id="298be-104"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 類別提供一種機制，可讓您執行自訂行為，並將其套用至來自手寫筆裝置的資料流程，以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="298be-104">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> class provides a mechanism for you to implement custom behavior and apply it to the stream of data coming from the stylus device for the optimal performance.</span></span>  
  
 <span data-ttu-id="298be-105">本主題包含下列各小節：</span><span class="sxs-lookup"><span data-stu-id="298be-105">This topic contains the following subsections:</span></span>  
  
- [<span data-ttu-id="298be-106">架構</span><span class="sxs-lookup"><span data-stu-id="298be-106">Architecture</span></span>](#Architecture)  
  
- [<span data-ttu-id="298be-107">執行手寫筆外掛程式</span><span class="sxs-lookup"><span data-stu-id="298be-107">Implementing Stylus Plug-ins</span></span>](#ImplementingStylusPlugins)  
  
- [<span data-ttu-id="298be-108">將外掛程式新增至 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="298be-108">Adding Your Plug-in to an InkCanvas</span></span>](#AddingYourPluginToAnInkCanvas)  
  
- [<span data-ttu-id="298be-109">結論</span><span class="sxs-lookup"><span data-stu-id="298be-109">Conclusion</span></span>](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a><span data-ttu-id="298be-110">架構</span><span class="sxs-lookup"><span data-stu-id="298be-110">Architecture</span></span>  
 <span data-ttu-id="298be-111"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 是[StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) api 的演進，如[存取和操作手寫筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))中所述。</span><span class="sxs-lookup"><span data-stu-id="298be-111">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> is the evolution of the [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) APIs, described in [Accessing and Manipulating Pen Input](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="298be-112">每個 <xref:System.Windows.UIElement> 都有一個 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="298be-112">Each <xref:System.Windows.UIElement> has a <xref:System.Windows.UIElement.StylusPlugIns%2A> property that is a <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span> <span data-ttu-id="298be-113">您可以將 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 新增至專案的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性，以操作產生的 <xref:System.Windows.Input.StylusPoint> 資料。</span><span class="sxs-lookup"><span data-stu-id="298be-113">You can add a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> to an element's <xref:System.Windows.UIElement.StylusPlugIns%2A> property to manipulate <xref:System.Windows.Input.StylusPoint> data as it is generated.</span></span> <span data-ttu-id="298be-114"><xref:System.Windows.Input.StylusPoint> 資料是由系統數位板支援的所有屬性所組成，包括 <xref:System.Windows.Input.StylusPoint.X%2A> 和 <xref:System.Windows.Input.StylusPoint.Y%2A> 點資料，以及 <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> 資料。</span><span class="sxs-lookup"><span data-stu-id="298be-114"><xref:System.Windows.Input.StylusPoint> data consists of all the properties supported by the system digitizer, including the <xref:System.Windows.Input.StylusPoint.X%2A> and <xref:System.Windows.Input.StylusPoint.Y%2A> point data, as well as <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> data.</span></span>  
  
 <span data-ttu-id="298be-115">當您將 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性時，會將您的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 物件直接插入至來自 <xref:System.Windows.Input.Stylus> 裝置的資料串流。</span><span class="sxs-lookup"><span data-stu-id="298be-115">Your <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects are inserted directly into the stream of data coming from the <xref:System.Windows.Input.Stylus> device when you add the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span> <span data-ttu-id="298be-116">外掛程式新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合的順序，會決定它們接收 <xref:System.Windows.Input.StylusPoint> 資料的順序。</span><span class="sxs-lookup"><span data-stu-id="298be-116">The order in which plug-ins are added to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection dictates the order in which they will receive <xref:System.Windows.Input.StylusPoint> data.</span></span> <span data-ttu-id="298be-117">例如，如果您加入的篩選外掛程式會將輸入限制在特定區域，然後新增外掛程式來辨識寫入的筆勢，則可辨識手勢的外掛程式將會接收篩選的 <xref:System.Windows.Input.StylusPoint> 資料。</span><span class="sxs-lookup"><span data-stu-id="298be-117">For example, if you add a filter plug-in that restricts input to a particular region, and then add a plug-in that recognizes gestures as they are written, the plug-in that recognizes gestures will receive filtered <xref:System.Windows.Input.StylusPoint> data.</span></span>  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a><span data-ttu-id="298be-118">執行手寫筆外掛程式</span><span class="sxs-lookup"><span data-stu-id="298be-118">Implementing Stylus Plug-ins</span></span>  
 <span data-ttu-id="298be-119">若要執行外掛程式，請從 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>衍生一個類別。</span><span class="sxs-lookup"><span data-stu-id="298be-119">To implement a plug-in, derive a class from <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.</span></span> <span data-ttu-id="298be-120">此類別會套用至從 <xref:System.Windows.Input.Stylus>傳入的資料流程。</span><span class="sxs-lookup"><span data-stu-id="298be-120">This class is applied o the stream of data as it comes in from the <xref:System.Windows.Input.Stylus>.</span></span> <span data-ttu-id="298be-121">在此類別中，您可以修改 <xref:System.Windows.Input.StylusPoint> 資料的值。</span><span class="sxs-lookup"><span data-stu-id="298be-121">In this class you can modify the values of the <xref:System.Windows.Input.StylusPoint> data.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="298be-122">如果 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 擲回或造成例外狀況，應用程式將會關閉。</span><span class="sxs-lookup"><span data-stu-id="298be-122">If a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> throws or causes an exception, the application will close.</span></span> <span data-ttu-id="298be-123">您應該徹底測試使用 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 的控制項，而且只有在您確定 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 不會擲回例外狀況時，才使用控制項。</span><span class="sxs-lookup"><span data-stu-id="298be-123">You should thoroughly test controls that consume a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and only use a control if you are certain the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> will not throw an exception.</span></span>  
  
 <span data-ttu-id="298be-124">下列範例示範的外掛程式會藉由修改來自 <xref:System.Windows.Input.Stylus> 裝置的 <xref:System.Windows.Input.StylusPoint> 資料中的 <xref:System.Windows.Input.StylusPoint.X%2A> 和 <xref:System.Windows.Input.StylusPoint.Y%2A> 值，來限制手寫筆輸入。</span><span class="sxs-lookup"><span data-stu-id="298be-124">The following example demonstrates a plug-in that restricts the stylus input by modifying the <xref:System.Windows.Input.StylusPoint.X%2A> and <xref:System.Windows.Input.StylusPoint.Y%2A> values in the <xref:System.Windows.Input.StylusPoint> data as it comes in from the <xref:System.Windows.Input.Stylus> device.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a><span data-ttu-id="298be-125">將外掛程式新增至 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="298be-125">Adding Your Plug-in to an InkCanvas</span></span>  
 <span data-ttu-id="298be-126">使用您的自訂外掛程式最簡單的方式，就是執行衍生自 InkCanvas 的類別，並將它新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="298be-126">The easiest way to use your custom plug-in is to implement a class that derives from InkCanvas and add it to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span>  
  
 <span data-ttu-id="298be-127">下列範例示範用來篩選筆墨的自訂 <xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="298be-127">The following example demonstrates a custom <xref:System.Windows.Controls.InkCanvas> that filters the ink.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 <span data-ttu-id="298be-128">如果您將 `FilterInkCanvas` 新增至應用程式並加以執行，您會注意到，在使用者完成筆劃之前，筆跡不會限制為區域。</span><span class="sxs-lookup"><span data-stu-id="298be-128">If you add a `FilterInkCanvas` to your application and run it, you will notice that the ink isn't restricted to a region until after the user completes a stroke.</span></span> <span data-ttu-id="298be-129">這是因為 <xref:System.Windows.Controls.InkCanvas> 具有 <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> 屬性，這是 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，而且已經是 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合的成員。</span><span class="sxs-lookup"><span data-stu-id="298be-129">This is because the <xref:System.Windows.Controls.InkCanvas> has a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property, which is a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> and is already a member of the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection.</span></span> <span data-ttu-id="298be-130">您在 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合中新增的自訂 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 會在 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 接收資料之後收到 <xref:System.Windows.Input.StylusPoint> 的資料。</span><span class="sxs-lookup"><span data-stu-id="298be-130">The custom <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> you added to the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection receives the <xref:System.Windows.Input.StylusPoint> data after <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives data.</span></span> <span data-ttu-id="298be-131">因此，在使用者提起畫筆以結束筆劃之前，不會篩選 <xref:System.Windows.Input.StylusPoint> 的資料。</span><span class="sxs-lookup"><span data-stu-id="298be-131">As a result, the <xref:System.Windows.Input.StylusPoint> data will not be filtered until after the user lifts the pen to end a stroke.</span></span> <span data-ttu-id="298be-132">若要在使用者繪製時篩選筆墨，您必須在 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>之前插入 `FilterPlugin`。</span><span class="sxs-lookup"><span data-stu-id="298be-132">To filter the ink as the user draws it, you must insert the `FilterPlugin` before the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span>  
  
 <span data-ttu-id="298be-133">下列C#程式碼示範的自訂 <xref:System.Windows.Controls.InkCanvas> 會在繪製時篩選筆墨。</span><span class="sxs-lookup"><span data-stu-id="298be-133">The following C# code demonstrates a custom <xref:System.Windows.Controls.InkCanvas> that filters the ink as it is drawn.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="298be-134">結論</span><span class="sxs-lookup"><span data-stu-id="298be-134">Conclusion</span></span>  
 <span data-ttu-id="298be-135">藉由衍生您自己的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 類別，並將它們插入 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 集合中，您可以大幅增強數位筆跡的行為。</span><span class="sxs-lookup"><span data-stu-id="298be-135">By deriving your own <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes and inserting them into <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> collections, you can greatly enhance the behavior of your digital ink.</span></span> <span data-ttu-id="298be-136">您可以存取所產生的 <xref:System.Windows.Input.StylusPoint> 資料，讓您有機會自訂 <xref:System.Windows.Input.Stylus> 輸入。</span><span class="sxs-lookup"><span data-stu-id="298be-136">You have access to the <xref:System.Windows.Input.StylusPoint> data as it is generated, giving you the opportunity to customize the <xref:System.Windows.Input.Stylus> input.</span></span> <span data-ttu-id="298be-137">因為您有 <xref:System.Windows.Input.StylusPoint> 資料的低層級存取權，所以您可以使用應用程式的最佳效能來執行筆墨集合和轉譯。</span><span class="sxs-lookup"><span data-stu-id="298be-137">Because you have such low-level access to the <xref:System.Windows.Input.StylusPoint> data, you can implement ink collection and rendering with optimal performance for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="298be-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="298be-138">See also</span></span>

- [<span data-ttu-id="298be-139">筆跡進階處理</span><span class="sxs-lookup"><span data-stu-id="298be-139">Advanced Ink Handling</span></span>](advanced-ink-handling.md)
- <span data-ttu-id="298be-140">[存取和操作手寫筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="298be-140">[Accessing and Manipulating Pen Input](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))</span></span>
