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
ms.openlocfilehash: 621684e14f9d1b599c4ef60e3731f0f58f31aacd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740170"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a><span data-ttu-id="df324-102">教學課程：在 Win32 應用程式中裝載視覺物件</span><span class="sxs-lookup"><span data-stu-id="df324-102">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="df324-103">提供用來建立應用程式的豐富環境。</span><span class="sxs-lookup"><span data-stu-id="df324-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="df324-104">不過，當您在 Win32 程式碼中投入大量投資時，將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能加入至應用程式，而不是重寫您的程式碼，可能會更有效率。</span><span class="sxs-lookup"><span data-stu-id="df324-104">However, when you have a substantial investment in Win32 code, it might be more effective to add [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] functionality to your application rather than rewrite your code.</span></span> <span data-ttu-id="df324-105">為了提供應用程式中同時使用之 Win32 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形子系統的支援，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供在 Win32 視窗中裝載物件的機制。</span><span class="sxs-lookup"><span data-stu-id="df324-105">To provide support for Win32 and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphics subsystems used concurrently in an application, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a mechanism for hosting objects in a Win32 window.</span></span>  
  
 <span data-ttu-id="df324-106">本教學課程說明如何撰寫範例應用程式，[使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)，它會在 win32 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的視覺物件。</span><span class="sxs-lookup"><span data-stu-id="df324-106">This tutorial describes how to write a sample application, [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995), that hosts [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual objects in a Win32 window.</span></span>  

<a name="requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="df324-107">需求</span><span class="sxs-lookup"><span data-stu-id="df324-107">Requirements</span></span>  
 <span data-ttu-id="df324-108">本教學課程假設您已熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 Win32 程式設計的基本概念。</span><span class="sxs-lookup"><span data-stu-id="df324-108">This tutorial assumes a basic familiarity with both [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and Win32 programming.</span></span> <span data-ttu-id="df324-109">如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計的基本簡介，請參閱[逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="df324-109">For a basic introduction to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programming, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span> <span data-ttu-id="df324-110">如需 Win32 程式設計的簡介，請參閱主題中的任何一本書，特別是 Charles Petzold 的程式*設計視窗*。</span><span class="sxs-lookup"><span data-stu-id="df324-110">For an introduction to Win32 programming, see any of the numerous books on the subject, in particular *Programming Windows* by Charles Petzold.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df324-111">本教學課程包含一些來自相關範例的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="df324-111">This tutorial includes a number of code examples from the associated sample.</span></span> <span data-ttu-id="df324-112">不過，為了方便閱讀，並未包含完整的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="df324-112">However, for readability, it does not include the complete sample code.</span></span> <span data-ttu-id="df324-113">如需完整的範例程式碼，請參閱[使用 Win32 交互操作進行點擊測試範例](https://go.microsoft.com/fwlink/?LinkID=159995)。</span><span class="sxs-lookup"><span data-stu-id="df324-113">For the complete sample code, see [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a><span data-ttu-id="df324-114">建立 Win32 主機視窗</span><span class="sxs-lookup"><span data-stu-id="df324-114">Creating the Host Win32 Window</span></span>  
 <span data-ttu-id="df324-115">在 Win32 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件的關鍵是 <xref:System.Windows.Interop.HwndSource> 類別。</span><span class="sxs-lookup"><span data-stu-id="df324-115">The key to hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objects in a Win32 window is the <xref:System.Windows.Interop.HwndSource> class.</span></span> <span data-ttu-id="df324-116">這個類別會將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件包裝在 Win32 視窗中，以便將它們併入您的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 做為子視窗。</span><span class="sxs-lookup"><span data-stu-id="df324-116">This class wraps the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objects in a Win32 window, allowing them to be incorporated into your [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] as a child window.</span></span>  
  
 <span data-ttu-id="df324-117">下列範例顯示用來建立 <xref:System.Windows.Interop.HwndSource> 物件做為視覺物件之 Win32 容器視窗的程式碼。</span><span class="sxs-lookup"><span data-stu-id="df324-117">The following example shows the code for creating the <xref:System.Windows.Interop.HwndSource> object as the Win32 container window for the visual objects.</span></span> <span data-ttu-id="df324-118">若要設定 Win32 視窗的視窗樣式、位置和其他參數，請使用 <xref:System.Windows.Interop.HwndSourceParameters> 物件。</span><span class="sxs-lookup"><span data-stu-id="df324-118">To set the window style, position, and other parameters for the Win32 window, use the <xref:System.Windows.Interop.HwndSourceParameters> object.</span></span>  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> <span data-ttu-id="df324-119"><xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> 屬性的值不能設定為 WS_EX_TRANSPARENT。</span><span class="sxs-lookup"><span data-stu-id="df324-119">The value of the <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> property cannot be set to WS_EX_TRANSPARENT.</span></span> <span data-ttu-id="df324-120">這表示主機 Win32 視窗不可以是透明的。</span><span class="sxs-lookup"><span data-stu-id="df324-120">This means that the host Win32 window cannot be transparent.</span></span> <span data-ttu-id="df324-121">因此，[主機 Win32] 視窗的背景色彩會設定為與父視窗相同的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="df324-121">For this reason, the background color of the host Win32 window is set to the same background color as its parent window.</span></span>  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a><span data-ttu-id="df324-122">將視覺物件加入至主機 Win32 視窗</span><span class="sxs-lookup"><span data-stu-id="df324-122">Adding Visual Objects to the Host Win32 Window</span></span>  
 <span data-ttu-id="df324-123">建立視覺物件的 [主機 Win32 容器] 視窗之後，您就可以在其中加入視覺物件。</span><span class="sxs-lookup"><span data-stu-id="df324-123">Once you have created a host Win32 container window for the visual objects, you can add visual objects to it.</span></span> <span data-ttu-id="df324-124">您會想要確保視覺物件的任何轉換（例如動畫）不會延伸超過主機 Win32 視窗周框的範圍。</span><span class="sxs-lookup"><span data-stu-id="df324-124">You will want to ensure that any transformations of the visual objects, such as animations, do not extend beyond the bounds of the host Win32 window's bounding rectangle.</span></span>  
  
 <span data-ttu-id="df324-125">下列範例顯示用來建立 <xref:System.Windows.Interop.HwndSource> 物件以及在其中加入視覺物件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="df324-125">The following example shows the code for creating the <xref:System.Windows.Interop.HwndSource> object and adding visual objects to it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df324-126"><xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性會設定為新增至 [主機 Win32] 視窗的第一個視覺物件。</span><span class="sxs-lookup"><span data-stu-id="df324-126">The <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object is set to the first visual object added to the host Win32 window.</span></span> <span data-ttu-id="df324-127">根視覺物件會定義視覺物件樹狀結構的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="df324-127">The root visual object defines the top-most node of the visual object tree.</span></span> <span data-ttu-id="df324-128">加入至 [主機 Win32] 視窗的任何後續視覺物件都會加入為子物件。</span><span class="sxs-lookup"><span data-stu-id="df324-128">Any subsequent visual objects added to the host Win32 window are added as child objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a><span data-ttu-id="df324-129">實作 Win32 訊息篩選器</span><span class="sxs-lookup"><span data-stu-id="df324-129">Implementing the Win32 Message Filter</span></span>  
 <span data-ttu-id="df324-130">視覺物件的 [主機 Win32] 視窗需要視窗訊息篩選程式，以處理從應用程式佇列傳送至視窗的訊息。</span><span class="sxs-lookup"><span data-stu-id="df324-130">The host Win32 window for the visual objects requires a window message filter procedure to handle messages that are sent to the window from the application queue.</span></span> <span data-ttu-id="df324-131">視窗程式會接收來自 Win32 系統的訊息。</span><span class="sxs-lookup"><span data-stu-id="df324-131">The window procedure receives messages from the Win32 system.</span></span> <span data-ttu-id="df324-132">這些可能是輸入訊息或視窗管理訊息。</span><span class="sxs-lookup"><span data-stu-id="df324-132">These may be input messages or window-management messages.</span></span> <span data-ttu-id="df324-133">您可以選擇性地在您的視窗程序中處理訊息，或者將訊息傳遞至系統進行預設處理。</span><span class="sxs-lookup"><span data-stu-id="df324-133">You can optionally handle a message in your window procedure or pass the message to the system for default processing.</span></span>  
  
 <span data-ttu-id="df324-134">您定義為視覺物件之父系的 <xref:System.Windows.Interop.HwndSource> 物件必須參考您提供的視窗訊息篩選程式。</span><span class="sxs-lookup"><span data-stu-id="df324-134">The <xref:System.Windows.Interop.HwndSource> object that you defined as the parent for the visual objects must reference the window message filter procedure you provide.</span></span> <span data-ttu-id="df324-135">當您建立 <xref:System.Windows.Interop.HwndSource> 物件時，請將 <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> 屬性設定為參考視窗程式。</span><span class="sxs-lookup"><span data-stu-id="df324-135">When you create the <xref:System.Windows.Interop.HwndSource> object, set the <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> property to reference the window procedure.</span></span>  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 <span data-ttu-id="df324-136">下列範例顯示用來處理滑鼠左右按鈕訊息的程式碼。</span><span class="sxs-lookup"><span data-stu-id="df324-136">The following example shows the code for handling the left and right mouse button up messages.</span></span> <span data-ttu-id="df324-137">滑鼠點擊位置的座標值包含在 `lParam` 參數的值中。</span><span class="sxs-lookup"><span data-stu-id="df324-137">The coordinate value of the mouse hit position is contained in the value of the `lParam` parameter.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a><span data-ttu-id="df324-138">處理 Win32 訊息</span><span class="sxs-lookup"><span data-stu-id="df324-138">Processing the Win32 Messages</span></span>  
 <span data-ttu-id="df324-139">下列範例中的程式碼顯示如何針對主機 Win32 視窗中包含的視覺物件階層架構執行點擊測試。</span><span class="sxs-lookup"><span data-stu-id="df324-139">The code in the following example shows how a hit test is performed against the hierarchy of visual objects contained in the host Win32 window.</span></span> <span data-ttu-id="df324-140">您可以使用 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 方法來指定根視覺物件和要進行點擊測試的座標值，以識別某個點是否在視覺物件的幾何內。</span><span class="sxs-lookup"><span data-stu-id="df324-140">You can identify whether a point is within the geometry of a visual object, by using the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to specify the root visual object and the coordinate value to hit test against.</span></span> <span data-ttu-id="df324-141">在此情況下，根視覺物件是 <xref:System.Windows.Interop.HwndSource> 物件之 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="df324-141">In this case, the root visual object is the value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="df324-142">如需針對視覺物件進行點擊測試的詳細資訊，請參閱[視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="df324-142">For more information on hit testing against visual objects, see [Hit Testing in the Visual Layer](hit-testing-in-the-visual-layer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df324-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="df324-143">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="df324-144">使用 Win32 交互操作進行點擊測試範例</span><span class="sxs-lookup"><span data-stu-id="df324-144">Hit Test with Win32 Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159995)
- [<span data-ttu-id="df324-145">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="df324-145">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
