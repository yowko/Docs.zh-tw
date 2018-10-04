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
ms.openlocfilehash: 935999fd5ada93bedebb38462f9faa93b8ec923f
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781475"
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="bfd38-102">逐步解說：建立您的第一個觸控應用程式</span><span class="sxs-lookup"><span data-stu-id="bfd38-102">Walkthrough: Creating Your First Touch Application</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="bfd38-103">讓應用程式回應觸控。</span><span class="sxs-lookup"><span data-stu-id="bfd38-103"> enables applications to respond to touch.</span></span> <span data-ttu-id="bfd38-104">比方說，您可以使用其中一個互動應用程式或更多根手指觸控感應裝置，例如本逐步解說中建立的應用程式，可讓使用者移動觸控螢幕上調整大小，或使用觸控旋轉單一物件。</span><span class="sxs-lookup"><span data-stu-id="bfd38-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bfd38-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="bfd38-105">Prerequisites</span></span>  
 <span data-ttu-id="bfd38-106">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="bfd38-106">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="bfd38-107">Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="bfd38-107">Visual Studio.</span></span>  
  
-   <span data-ttu-id="bfd38-108">接受輸入，例如觸控螢幕，可支援 Windows Touch 的觸控裝置。</span><span class="sxs-lookup"><span data-stu-id="bfd38-108">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="bfd38-109">此外，您應該有基本的了解如何建立應用程式中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，尤其是如何訂閱和處理事件。</span><span class="sxs-lookup"><span data-stu-id="bfd38-109">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="bfd38-110">如需詳細資訊，請參閱[逐步解說︰我的第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd38-110">For more information, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="bfd38-111">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="bfd38-111">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="bfd38-112">若要建立應用程式</span><span class="sxs-lookup"><span data-stu-id="bfd38-112">To create the application</span></span>  
  
1.  <span data-ttu-id="bfd38-113">在 Visual Basic 或 Visual C# 中，建立名為 `BasicManipulation` 的新 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="bfd38-113">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="bfd38-114">如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。</span><span class="sxs-lookup"><span data-stu-id="bfd38-114">For more information, see [How to: Create a New WPF Application Project](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="bfd38-115">MainWindow.xaml 的內容取代為下列 XAML。</span><span class="sxs-lookup"><span data-stu-id="bfd38-115">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="bfd38-116">此標記會建立簡單的應用程式，其中包含紅色<xref:System.Windows.Shapes.Rectangle>上<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="bfd38-116">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="bfd38-117"><xref:System.Windows.UIElement.IsManipulationEnabled%2A>屬性<xref:System.Windows.Shapes.Rectangle>設為 true，因此它會接收操作事件。</span><span class="sxs-lookup"><span data-stu-id="bfd38-117">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="bfd38-118">應用程式訂閱<xref:System.Windows.UIElement.ManipulationStarting>， <xref:System.Windows.UIElement.ManipulationDelta>，和<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件。</span><span class="sxs-lookup"><span data-stu-id="bfd38-118">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="bfd38-119">這些事件包含邏輯來移動<xref:System.Windows.Shapes.Rectangle>使用者時操作它。</span><span class="sxs-lookup"><span data-stu-id="bfd38-119">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  <span data-ttu-id="bfd38-120">如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="BasicManipulation.MainWindow"`與`x:Class="MainWindow"`。</span><span class="sxs-lookup"><span data-stu-id="bfd38-120">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4.  <span data-ttu-id="bfd38-121">在 `MainWindow`類別中，新增下列<xref:System.Windows.UIElement.ManipulationStarting>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bfd38-121">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="bfd38-122"><xref:System.Windows.UIElement.ManipulationStarting>就會發生事件時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]偵測到該觸控輸入開始操作的物件。</span><span class="sxs-lookup"><span data-stu-id="bfd38-122">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="bfd38-123">程式碼會指定操作位置應該是相對於<xref:System.Windows.Window>藉由設定<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="bfd38-123">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]

5.  <span data-ttu-id="bfd38-124">在 `MainWindow`類別中，新增下列<xref:System.Windows.Input.ManipulationDelta>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bfd38-124">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>

     <span data-ttu-id="bfd38-125"><xref:System.Windows.Input.ManipulationDelta>觸控輸入變更位置，並可於操作期間發生多次時，就會發生事件。</span><span class="sxs-lookup"><span data-stu-id="bfd38-125">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="bfd38-126">手指引發之後，也會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="bfd38-126">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="bfd38-127">例如，如果使用者的螢幕上拖曳手指<xref:System.Windows.Input.ManipulationDelta>手指移事件會發生一次。</span><span class="sxs-lookup"><span data-stu-id="bfd38-127">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="bfd38-128">當使用者引發從畫面中，手指<xref:System.Windows.Input.ManipulationDelta>事件持續發生，模擬慣性。</span><span class="sxs-lookup"><span data-stu-id="bfd38-128">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>

     <span data-ttu-id="bfd38-129">程式碼會套用<xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>要<xref:System.Windows.UIElement.RenderTransform%2A>的<xref:System.Windows.Shapes.Rectangle>移動它，當使用者移動觸控輸入。</span><span class="sxs-lookup"><span data-stu-id="bfd38-129">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="bfd38-130">它也會檢查是否<xref:System.Windows.Shapes.Rectangle>超出範圍<xref:System.Windows.Window>在慣性期間的事件發生時。</span><span class="sxs-lookup"><span data-stu-id="bfd38-130">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="bfd38-131">因此，應用程式呼叫如果<xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType>方法以結束操作。</span><span class="sxs-lookup"><span data-stu-id="bfd38-131">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>

     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]

6.  <span data-ttu-id="bfd38-132">在 `MainWindow`類別中，新增下列<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bfd38-132">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>

     <span data-ttu-id="bfd38-133"><xref:System.Windows.UIElement.ManipulationInertiaStarting>事件發生於使用者引發從畫面的所有根手指。</span><span class="sxs-lookup"><span data-stu-id="bfd38-133">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="bfd38-134">程式碼設定的初始速度和移動、 擴充和旋轉該矩形的減速。</span><span class="sxs-lookup"><span data-stu-id="bfd38-134">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>

     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]

7.  <span data-ttu-id="bfd38-135">建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="bfd38-135">Build and run the project.</span></span>

     <span data-ttu-id="bfd38-136">您應該會看到視窗中顯示為紅色方形。</span><span class="sxs-lookup"><span data-stu-id="bfd38-136">You should see a red square appear in the window.</span></span>

## <a name="testing-the-application"></a><span data-ttu-id="bfd38-137">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="bfd38-137">Testing the Application</span></span>
 <span data-ttu-id="bfd38-138">若要測試應用程式，請嘗試下列操作。</span><span class="sxs-lookup"><span data-stu-id="bfd38-138">To test the application, try the following manipulations.</span></span> <span data-ttu-id="bfd38-139">請注意，您可以多個下列其中之一在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="bfd38-139">Note that you can do more than one of the following at the same time.</span></span>

-   <span data-ttu-id="bfd38-140">若要移動<xref:System.Windows.Shapes.Rectangle>，將手指放<xref:System.Windows.Shapes.Rectangle>並將手指移動螢幕上。</span><span class="sxs-lookup"><span data-stu-id="bfd38-140">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>

-   <span data-ttu-id="bfd38-141">若要調整大小<xref:System.Windows.Shapes.Rectangle>，將兩隻手指放在<xref:System.Windows.Shapes.Rectangle>，然後將手指，更接近手指或分開彼此。</span><span class="sxs-lookup"><span data-stu-id="bfd38-141">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>

-   <span data-ttu-id="bfd38-142">若要旋轉<xref:System.Windows.Shapes.Rectangle>，將兩隻手指放在<xref:System.Windows.Shapes.Rectangle>並旋轉手指。</span><span class="sxs-lookup"><span data-stu-id="bfd38-142">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>

 <span data-ttu-id="bfd38-143">若要使慣性，快速將引發手指已離開螢幕當您執行先前的操作。</span><span class="sxs-lookup"><span data-stu-id="bfd38-143">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="bfd38-144"><xref:System.Windows.Shapes.Rectangle>會繼續移動、 調整大小或旋轉幾秒鐘的時間之前就會停止。</span><span class="sxs-lookup"><span data-stu-id="bfd38-144">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfd38-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd38-145">See Also</span></span>

- <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>