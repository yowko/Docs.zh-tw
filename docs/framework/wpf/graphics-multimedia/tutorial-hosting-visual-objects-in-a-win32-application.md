---
title: 教學課程：在 Win32 應用程式中裝載視覺物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: d04357e0770bbf8eebe8f40a86a19ddc9baae3ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187432"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a><span data-ttu-id="5877d-102">教學課程：在 Win32 應用程式中裝載視覺物件</span><span class="sxs-lookup"><span data-stu-id="5877d-102">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="5877d-103">提供用來建立應用程式的豐富環境。</span><span class="sxs-lookup"><span data-stu-id="5877d-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="5877d-104">但是，當您對 Win32 代碼進行大量投資時，向應用程式添加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]功能而不是重寫代碼可能更有效。</span><span class="sxs-lookup"><span data-stu-id="5877d-104">However, when you have a substantial investment in Win32 code, it might be more effective to add [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] functionality to your application rather than rewrite your code.</span></span> <span data-ttu-id="5877d-105">要支援應用程式中同時使用的 Win32 和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]圖形子系統，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]請提供一種在 Win32 視窗中託管物件的機制。</span><span class="sxs-lookup"><span data-stu-id="5877d-105">To provide support for Win32 and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphics subsystems used concurrently in an application, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a mechanism for hosting objects in a Win32 window.</span></span>  
  
 <span data-ttu-id="5877d-106">本教程介紹如何編寫應用程式範例，[即使用 Win32 交互操作示例進行點擊測試](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)，該[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]示例在 Win32 視窗中承載可視物件。</span><span class="sxs-lookup"><span data-stu-id="5877d-106">This tutorial describes how to write a sample application, [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting), that hosts [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual objects in a Win32 window.</span></span>  

<a name="requirements"></a>
## <a name="requirements"></a><span data-ttu-id="5877d-107">需求</span><span class="sxs-lookup"><span data-stu-id="5877d-107">Requirements</span></span>  
 <span data-ttu-id="5877d-108">本教程假定對 Win32[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計和 Win32 程式設計基本熟悉。</span><span class="sxs-lookup"><span data-stu-id="5877d-108">This tutorial assumes a basic familiarity with both [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and Win32 programming.</span></span> <span data-ttu-id="5877d-109">有關[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式設計的基本介紹，請參閱[演練：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5877d-109">For a basic introduction to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programming, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span> <span data-ttu-id="5877d-110">有關 Win32 程式設計的介紹，請參閱有關該主題的眾多書籍中的任何一本書，特別是查理斯·佩佐德的*程式設計 Windows。*</span><span class="sxs-lookup"><span data-stu-id="5877d-110">For an introduction to Win32 programming, see any of the numerous books on the subject, in particular *Programming Windows* by Charles Petzold.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5877d-111">本教學課程包含一些來自相關範例的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="5877d-111">This tutorial includes a number of code examples from the associated sample.</span></span> <span data-ttu-id="5877d-112">不過，為了方便閱讀，並未包含完整的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="5877d-112">However, for readability, it does not include the complete sample code.</span></span> <span data-ttu-id="5877d-113">有關完整的示例代碼，請參閱[使用 Win32 交互操作示例進行點擊測試](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)。</span><span class="sxs-lookup"><span data-stu-id="5877d-113">For the complete sample code, see [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).</span></span>  
  
<a name="creating_the_host_win32_window"></a>
## <a name="creating-the-host-win32-window"></a><span data-ttu-id="5877d-114">建立 Win32 主機視窗</span><span class="sxs-lookup"><span data-stu-id="5877d-114">Creating the Host Win32 Window</span></span>  
 <span data-ttu-id="5877d-115">在 Win32 視窗中託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]物件的關鍵是<xref:System.Windows.Interop.HwndSource>類。</span><span class="sxs-lookup"><span data-stu-id="5877d-115">The key to hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objects in a Win32 window is the <xref:System.Windows.Interop.HwndSource> class.</span></span> <span data-ttu-id="5877d-116">此類將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]物件包裝在 Win32 視窗中，允許將它們作為子視窗合併到您的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]視窗中。</span><span class="sxs-lookup"><span data-stu-id="5877d-116">This class wraps the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objects in a Win32 window, allowing them to be incorporated into your [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] as a child window.</span></span>  
  
 <span data-ttu-id="5877d-117">下面的示例顯示了將<xref:System.Windows.Interop.HwndSource>物件創建為可視物件的 Win32 容器視窗的代碼。</span><span class="sxs-lookup"><span data-stu-id="5877d-117">The following example shows the code for creating the <xref:System.Windows.Interop.HwndSource> object as the Win32 container window for the visual objects.</span></span> <span data-ttu-id="5877d-118">要設置 Win32 視窗的視窗樣式、位置和其他參數，請使用 該<xref:System.Windows.Interop.HwndSourceParameters>物件。</span><span class="sxs-lookup"><span data-stu-id="5877d-118">To set the window style, position, and other parameters for the Win32 window, use the <xref:System.Windows.Interop.HwndSourceParameters> object.</span></span>  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> <span data-ttu-id="5877d-119">屬性的值<xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A>不能設置為WS_EX_TRANSPARENT。</span><span class="sxs-lookup"><span data-stu-id="5877d-119">The value of the <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> property cannot be set to WS_EX_TRANSPARENT.</span></span> <span data-ttu-id="5877d-120">這意味著主機 Win32 視窗不能透明。</span><span class="sxs-lookup"><span data-stu-id="5877d-120">This means that the host Win32 window cannot be transparent.</span></span> <span data-ttu-id="5877d-121">因此，主機 Win32 視窗的背景顏色設置為與其父視窗相同的背景顏色。</span><span class="sxs-lookup"><span data-stu-id="5877d-121">For this reason, the background color of the host Win32 window is set to the same background color as its parent window.</span></span>  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>
## <a name="adding-visual-objects-to-the-host-win32-window"></a><span data-ttu-id="5877d-122">將視覺物件加入至主機 Win32 視窗</span><span class="sxs-lookup"><span data-stu-id="5877d-122">Adding Visual Objects to the Host Win32 Window</span></span>  
 <span data-ttu-id="5877d-123">為可視物件創建主機 Win32 容器視窗後，可以向其添加可視物件。</span><span class="sxs-lookup"><span data-stu-id="5877d-123">Once you have created a host Win32 container window for the visual objects, you can add visual objects to it.</span></span> <span data-ttu-id="5877d-124">您需要確保視覺物件的任何轉換（如動畫）不會超出主機 Win32 視窗的邊界矩形的邊界範圍。</span><span class="sxs-lookup"><span data-stu-id="5877d-124">You will want to ensure that any transformations of the visual objects, such as animations, do not extend beyond the bounds of the host Win32 window's bounding rectangle.</span></span>  
  
 <span data-ttu-id="5877d-125">下面的示例顯示了用於創建<xref:System.Windows.Interop.HwndSource>物件和向物件添加可視物件的代碼。</span><span class="sxs-lookup"><span data-stu-id="5877d-125">The following example shows the code for creating the <xref:System.Windows.Interop.HwndSource> object and adding visual objects to it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5877d-126"><xref:System.Windows.Interop.HwndSource>物件<xref:System.Windows.Interop.HwndSource.RootVisual%2A>的屬性設置為添加到主機 Win32 視窗的第一個可視物件。</span><span class="sxs-lookup"><span data-stu-id="5877d-126">The <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object is set to the first visual object added to the host Win32 window.</span></span> <span data-ttu-id="5877d-127">根視覺物件會定義視覺物件樹狀結構的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="5877d-127">The root visual object defines the top-most node of the visual object tree.</span></span> <span data-ttu-id="5877d-128">添加到主機 Win32 視窗的任何後續可視物件都添加為子物件。</span><span class="sxs-lookup"><span data-stu-id="5877d-128">Any subsequent visual objects added to the host Win32 window are added as child objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>
## <a name="implementing-the-win32-message-filter"></a><span data-ttu-id="5877d-129">實作 Win32 訊息篩選器</span><span class="sxs-lookup"><span data-stu-id="5877d-129">Implementing the Win32 Message Filter</span></span>  
 <span data-ttu-id="5877d-130">視覺物件的主機 Win32 視窗需要視窗消息篩選器過程來處理從應用程式佇列發送到視窗的消息。</span><span class="sxs-lookup"><span data-stu-id="5877d-130">The host Win32 window for the visual objects requires a window message filter procedure to handle messages that are sent to the window from the application queue.</span></span> <span data-ttu-id="5877d-131">視窗過程接收來自 Win32 系統的消息。</span><span class="sxs-lookup"><span data-stu-id="5877d-131">The window procedure receives messages from the Win32 system.</span></span> <span data-ttu-id="5877d-132">這些可能是輸入訊息或視窗管理訊息。</span><span class="sxs-lookup"><span data-stu-id="5877d-132">These may be input messages or window-management messages.</span></span> <span data-ttu-id="5877d-133">您可以選擇性地在您的視窗程序中處理訊息，或者將訊息傳遞至系統進行預設處理。</span><span class="sxs-lookup"><span data-stu-id="5877d-133">You can optionally handle a message in your window procedure or pass the message to the system for default processing.</span></span>  
  
 <span data-ttu-id="5877d-134">您<xref:System.Windows.Interop.HwndSource>定義為可視物件的父物件必須引用您提供的視窗消息篩選器過程。</span><span class="sxs-lookup"><span data-stu-id="5877d-134">The <xref:System.Windows.Interop.HwndSource> object that you defined as the parent for the visual objects must reference the window message filter procedure you provide.</span></span> <span data-ttu-id="5877d-135">創建物件時，<xref:System.Windows.Interop.HwndSource>將<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>屬性設置為引用視窗過程。</span><span class="sxs-lookup"><span data-stu-id="5877d-135">When you create the <xref:System.Windows.Interop.HwndSource> object, set the <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> property to reference the window procedure.</span></span>  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 <span data-ttu-id="5877d-136">下列範例顯示用來處理滑鼠左右按鈕訊息的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5877d-136">The following example shows the code for handling the left and right mouse button up messages.</span></span> <span data-ttu-id="5877d-137">滑鼠命中位置的座標值包含在`lParam`參數的值中。</span><span class="sxs-lookup"><span data-stu-id="5877d-137">The coordinate value of the mouse hit position is contained in the value of the `lParam` parameter.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>
## <a name="processing-the-win32-messages"></a><span data-ttu-id="5877d-138">處理 Win32 訊息</span><span class="sxs-lookup"><span data-stu-id="5877d-138">Processing the Win32 Messages</span></span>  
 <span data-ttu-id="5877d-139">以下示例中的代碼顯示如何針對主機 Win32 視窗中中包含的可視物件的層次結構執行點擊測試。</span><span class="sxs-lookup"><span data-stu-id="5877d-139">The code in the following example shows how a hit test is performed against the hierarchy of visual objects contained in the host Win32 window.</span></span> <span data-ttu-id="5877d-140">通過使用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法指定根可視物件和要點擊測試的座標值，可以識別點是否位於可視物件的幾何體內。</span><span class="sxs-lookup"><span data-stu-id="5877d-140">You can identify whether a point is within the geometry of a visual object, by using the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to specify the root visual object and the coordinate value to hit test against.</span></span> <span data-ttu-id="5877d-141">在這種情況下，根可視物件是<xref:System.Windows.Interop.HwndSource.RootVisual%2A><xref:System.Windows.Interop.HwndSource>物件屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5877d-141">In this case, the root visual object is the value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="5877d-142">有關針對可視物件進行點擊測試的詳細資訊，請參閱[視覺化圖層中的點擊測試](hit-testing-in-the-visual-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="5877d-142">For more information on hit testing against visual objects, see [Hit Testing in the Visual Layer](hit-testing-in-the-visual-layer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5877d-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5877d-143">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="5877d-144">使用 Win32 交互操作進行點擊測試範例 (英文)</span><span class="sxs-lookup"><span data-stu-id="5877d-144">Hit Test with Win32 Interoperation Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [<span data-ttu-id="5877d-145">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="5877d-145">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
