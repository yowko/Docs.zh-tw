---
title: 逐步解說：建立您的第一個觸控應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: 94a97c30179f7a8231426e31b8cacc364629ffc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548347"
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="66584-102">逐步解說：建立您的第一個觸控應用程式</span><span class="sxs-lookup"><span data-stu-id="66584-102">Walkthrough: Creating Your First Touch Application</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="66584-103"> 可讓應用程式要碰觸的回應。</span><span class="sxs-lookup"><span data-stu-id="66584-103"> enables applications to respond to touch.</span></span> <span data-ttu-id="66584-104">例如，您可以使用其中一個應用程式與互動或觸控式裝置，例如本逐步解說建立的應用程式，可讓使用者移動，觸控螢幕上的多個指調整大小或旋轉使用觸控的單一物件。</span><span class="sxs-lookup"><span data-stu-id="66584-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="66584-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="66584-105">Prerequisites</span></span>  
 <span data-ttu-id="66584-106">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="66584-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]<span data-ttu-id="66584-107">.</span><span class="sxs-lookup"><span data-stu-id="66584-107">.</span></span>  
  
-   <span data-ttu-id="66584-108">Windows 7。</span><span class="sxs-lookup"><span data-stu-id="66584-108">Windows 7.</span></span>  
  
-   <span data-ttu-id="66584-109">接受觸控輸入，例如觸控螢幕，可支援 Windows 觸控裝置。</span><span class="sxs-lookup"><span data-stu-id="66584-109">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="66584-110">此外，您應該有基本了解如何建立應用程式中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，特別是如何訂閱和處理事件。</span><span class="sxs-lookup"><span data-stu-id="66584-110">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="66584-111">如需詳細資訊，請參閱[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="66584-111">For more information, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="66584-112">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="66584-112">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="66584-113">若要建立應用程式</span><span class="sxs-lookup"><span data-stu-id="66584-113">To create the application</span></span>  
  
1.  <span data-ttu-id="66584-114">在 Visual Basic 或 Visual C# 中，建立名為 `BasicManipulation` 的新 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="66584-114">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="66584-115">如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。</span><span class="sxs-lookup"><span data-stu-id="66584-115">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="66584-116">以下列 XAML 取代 MainWindow.xaml 的內容。</span><span class="sxs-lookup"><span data-stu-id="66584-116">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="66584-117">這個標記會建立簡單的應用程式，其中包含紅色<xref:System.Windows.Shapes.Rectangle>上<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="66584-117">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="66584-118"><xref:System.Windows.UIElement.IsManipulationEnabled%2A>屬性<xref:System.Windows.Shapes.Rectangle>設為 true，使其將接收管理事件。</span><span class="sxs-lookup"><span data-stu-id="66584-118">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="66584-119">應用程式訂閱<xref:System.Windows.UIElement.ManipulationStarting>， <xref:System.Windows.UIElement.ManipulationDelta>，和<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件。</span><span class="sxs-lookup"><span data-stu-id="66584-119">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="66584-120">這些事件包含邏輯，以移動<xref:System.Windows.Shapes.Rectangle>使用者時操作它。</span><span class="sxs-lookup"><span data-stu-id="66584-120">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  <span data-ttu-id="66584-121">如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="BasicManipulation.MainWindow"`與`x:Class="MainWindow"`。</span><span class="sxs-lookup"><span data-stu-id="66584-121">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4.  <span data-ttu-id="66584-122">在`MainWindow`類別，加入下列<xref:System.Windows.UIElement.ManipulationStarting>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="66584-122">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="66584-123"><xref:System.Windows.UIElement.ManipulationStarting>就會發生事件時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]偵測到該觸控輸入開始操作的物件。</span><span class="sxs-lookup"><span data-stu-id="66584-123">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="66584-124">程式碼會指定位置的操作應該相對於<xref:System.Windows.Window>藉由設定<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="66584-124">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  <span data-ttu-id="66584-125">在`MainWindow`類別，加入下列<xref:System.Windows.Input.ManipulationDelta>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="66584-125">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>  
  
     <span data-ttu-id="66584-126"><xref:System.Windows.Input.ManipulationDelta>觸控輸入變更位置，並可以操作期間發生多次時，就會發生事件。</span><span class="sxs-lookup"><span data-stu-id="66584-126">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="66584-127">引發手指之後，也會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="66584-127">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="66584-128">例如，如果使用者跨 畫面中，拖曳手指<xref:System.Windows.Input.ManipulationDelta>事件與手指移動出現多次。</span><span class="sxs-lookup"><span data-stu-id="66584-128">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="66584-129">當使用者引發畫面上，從手指<xref:System.Windows.Input.ManipulationDelta>模擬慣性持續發生的事件。</span><span class="sxs-lookup"><span data-stu-id="66584-129">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>  
  
     <span data-ttu-id="66584-130">程式碼適用於<xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>至<xref:System.Windows.UIElement.RenderTransform%2A>的<xref:System.Windows.Shapes.Rectangle>來移動它，當使用者移動觸控輸入。</span><span class="sxs-lookup"><span data-stu-id="66584-130">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="66584-131">它也會檢查是否<xref:System.Windows.Shapes.Rectangle>超出範圍<xref:System.Windows.Window>慣性期間發生的事件。</span><span class="sxs-lookup"><span data-stu-id="66584-131">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="66584-132">因此，應用程式呼叫如果<xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType>方法來中止操作。</span><span class="sxs-lookup"><span data-stu-id="66584-132">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  <span data-ttu-id="66584-133">在`MainWindow`類別，加入下列<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="66584-133">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>  
  
     <span data-ttu-id="66584-134"><xref:System.Windows.UIElement.ManipulationInertiaStarting>事件發生於使用者引發所有隻手指放在畫面上。</span><span class="sxs-lookup"><span data-stu-id="66584-134">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="66584-135">此程式碼設定的初始速度和減速移動、 擴充，以及矩形的旋轉。</span><span class="sxs-lookup"><span data-stu-id="66584-135">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  <span data-ttu-id="66584-136">建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="66584-136">Build and run the project.</span></span>  
  
     <span data-ttu-id="66584-137">您應該會看到在視窗中顯示為紅色方形。</span><span class="sxs-lookup"><span data-stu-id="66584-137">You should see a red square appear in the window.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="66584-138">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="66584-138">Testing the Application</span></span>  
 <span data-ttu-id="66584-139">若要測試應用程式，請嘗試下列操作。</span><span class="sxs-lookup"><span data-stu-id="66584-139">To test the application, try the following manipulations.</span></span> <span data-ttu-id="66584-140">請注意，您可以多個下列其中之一在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="66584-140">Note that you can do more than one of the following at the same time.</span></span>  
  
-   <span data-ttu-id="66584-141">若要移動<xref:System.Windows.Shapes.Rectangle>，打手指<xref:System.Windows.Shapes.Rectangle>和手指移動螢幕上。</span><span class="sxs-lookup"><span data-stu-id="66584-141">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>  
  
-   <span data-ttu-id="66584-142">若要調整大小<xref:System.Windows.Shapes.Rectangle>，兩隻手指放置於<xref:System.Windows.Shapes.Rectangle>，然後將手指接近一起或彼此相距較遠。</span><span class="sxs-lookup"><span data-stu-id="66584-142">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>  
  
-   <span data-ttu-id="66584-143">若要旋轉<xref:System.Windows.Shapes.Rectangle>，兩隻手指放置於<xref:System.Windows.Shapes.Rectangle>和旋轉的指周圍彼此。</span><span class="sxs-lookup"><span data-stu-id="66584-143">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>  
  
 <span data-ttu-id="66584-144">若要使慣性，快速引發從螢幕手指與您執行先前的操作。</span><span class="sxs-lookup"><span data-stu-id="66584-144">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="66584-145"><xref:System.Windows.Shapes.Rectangle>移動、 調整大小或旋轉數秒鐘，它會停止之前會繼續。</span><span class="sxs-lookup"><span data-stu-id="66584-145">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66584-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66584-146">See Also</span></span>  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
