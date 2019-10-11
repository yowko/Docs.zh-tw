---
title: 逐步解說：在 WPF 中排列 Windows Forms 控制項
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 3a94ef65be99b01a9511f37872cbcacd6ec12264
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179441"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="80bcd-102">逐步解說：在 WPF 中排列 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="80bcd-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="80bcd-103">本逐步解說將示範如何使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置功能來排列混合式應用程式中的 @no__t 1 控制項。</span><span class="sxs-lookup"><span data-stu-id="80bcd-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="80bcd-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="80bcd-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="80bcd-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="80bcd-105">Creating the project.</span></span>
- <span data-ttu-id="80bcd-106">使用預設的版面配置設定。</span><span class="sxs-lookup"><span data-stu-id="80bcd-106">Using default layout settings.</span></span>
- <span data-ttu-id="80bcd-107">依內容調整大小。</span><span class="sxs-lookup"><span data-stu-id="80bcd-107">Sizing to content.</span></span>
- <span data-ttu-id="80bcd-108">使用絕對位置。</span><span class="sxs-lookup"><span data-stu-id="80bcd-108">Using absolute positioning.</span></span>
- <span data-ttu-id="80bcd-109">明確指定大小。</span><span class="sxs-lookup"><span data-stu-id="80bcd-109">Specifying size explicitly.</span></span>
- <span data-ttu-id="80bcd-110">設定版面配置屬性。</span><span class="sxs-lookup"><span data-stu-id="80bcd-110">Setting layout properties.</span></span>
- <span data-ttu-id="80bcd-111">了解疊置順序的限制。</span><span class="sxs-lookup"><span data-stu-id="80bcd-111">Understanding z-order limitations.</span></span>
- <span data-ttu-id="80bcd-112">停駐。</span><span class="sxs-lookup"><span data-stu-id="80bcd-112">Docking.</span></span>
- <span data-ttu-id="80bcd-113">設定可見度。</span><span class="sxs-lookup"><span data-stu-id="80bcd-113">Setting visibility.</span></span>
- <span data-ttu-id="80bcd-114">裝載不會自動縮放的控制項。</span><span class="sxs-lookup"><span data-stu-id="80bcd-114">Hosting a control that does not stretch.</span></span>
- <span data-ttu-id="80bcd-115">縮放。</span><span class="sxs-lookup"><span data-stu-id="80bcd-115">Scaling.</span></span>
- <span data-ttu-id="80bcd-116">旋轉。</span><span class="sxs-lookup"><span data-stu-id="80bcd-116">Rotating.</span></span>
- <span data-ttu-id="80bcd-117">設定邊框距離及邊界。</span><span class="sxs-lookup"><span data-stu-id="80bcd-117">Setting padding and margins.</span></span>
- <span data-ttu-id="80bcd-118">使用動態版面配置容器。</span><span class="sxs-lookup"><span data-stu-id="80bcd-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="80bcd-119">如需本逐步解說中所述工作的完整程式代碼清單，請參閱[在 WPF 中排列 Windows Forms 控制項範例](https://go.microsoft.com/fwlink/?LinkID=159971)。</span><span class="sxs-lookup"><span data-stu-id="80bcd-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="80bcd-120">當您完成時，您將瞭解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構應用程式中的 @no__t 0 版面配置功能。</span><span class="sxs-lookup"><span data-stu-id="80bcd-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80bcd-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="80bcd-121">Prerequisites</span></span>

<span data-ttu-id="80bcd-122">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="80bcd-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="80bcd-123">建立專案</span><span class="sxs-lookup"><span data-stu-id="80bcd-123">Creating the Project</span></span>

<span data-ttu-id="80bcd-124">若要建立並設定專案，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-124">To create and set up the project, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-125">建立名為 `WpfLayoutHostingWf` 的 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="80bcd-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="80bcd-126">在方案總管中，新增下列元件的參考：</span><span class="sxs-lookup"><span data-stu-id="80bcd-126">In Solution Explorer, add references to the following assemblies:</span></span>

    - <span data-ttu-id="80bcd-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="80bcd-127">WindowsFormsIntegration</span></span>
    - <span data-ttu-id="80bcd-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="80bcd-128">System.Windows.Forms</span></span>
    - <span data-ttu-id="80bcd-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="80bcd-129">System.Drawing</span></span>

3. <span data-ttu-id="80bcd-130">按兩下 [ *mainwindow.xaml* ]，以 xaml 視圖開啟它。</span><span class="sxs-lookup"><span data-stu-id="80bcd-130">Double-click *MainWindow.xaml* to open it in XAML view.</span></span>

4. <span data-ttu-id="80bcd-131">在 <xref:System.Windows.Window> 元素中，新增下列 @no__t 1 命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="80bcd-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="80bcd-132">在 <xref:System.Windows.Controls.Grid> 元素中，將 <xref:System.Windows.Controls.Grid.ShowGridLines%2A> 屬性設定為 `true`，並定義五個數據列和三個數據行。</span><span class="sxs-lookup"><span data-stu-id="80bcd-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="80bcd-133">使用預設的版面配置設定</span><span class="sxs-lookup"><span data-stu-id="80bcd-133">Using Default Layout Settings</span></span>

<span data-ttu-id="80bcd-134">根據預設，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素會處理所裝載之 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的版面配置。</span><span class="sxs-lookup"><span data-stu-id="80bcd-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="80bcd-135">若要使用預設的版面配置設定，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-135">To use default layout settings, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-136">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="80bcd-137">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-137">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-138">@No__t-0 <xref:System.Windows.Forms.Button?displayProperty=nameWithType> 控制項會出現在 <xref:System.Windows.Controls.Canvas> 中。</span><span class="sxs-lookup"><span data-stu-id="80bcd-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="80bcd-139">裝載的控制項會根據其內容調整大小，而 @no__t 0 元素會調整大小以容納裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="80bcd-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="80bcd-140">依內容調整大小</span><span class="sxs-lookup"><span data-stu-id="80bcd-140">Sizing to Content</span></span>

<span data-ttu-id="80bcd-141">@No__t-0 元素可確保裝載的控制項已調整大小，以正確顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="80bcd-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

<span data-ttu-id="80bcd-142">若要將大小調整為內容，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-142">To size to content, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-143">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="80bcd-144">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-144">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-145">這兩個新的按鈕控制項會調整大小，以適當地顯示較長的文字字串和較大的字型大小，而 @no__t 0 元素會調整大小以容納裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="80bcd-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="80bcd-146">使用絕對位置</span><span class="sxs-lookup"><span data-stu-id="80bcd-146">Using Absolute Positioning</span></span>

<span data-ttu-id="80bcd-147">您可以使用絕對位置，將 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素放在使用者介面（UI）的任何位置。</span><span class="sxs-lookup"><span data-stu-id="80bcd-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

<span data-ttu-id="80bcd-148">若要使用絕對位置，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-148">To use absolute positioning, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-149">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="80bcd-150">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-150">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-151">@No__t-0 元素會從方格資料格的頂端放置20個圖元，左邊有20個圖元。</span><span class="sxs-lookup"><span data-stu-id="80bcd-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="80bcd-152">明確指定大小</span><span class="sxs-lookup"><span data-stu-id="80bcd-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="80bcd-153">您可以使用 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性來指定 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的大小。</span><span class="sxs-lookup"><span data-stu-id="80bcd-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

<span data-ttu-id="80bcd-154">若要明確指定大小，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-154">To specify size explicitly, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-155">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="80bcd-156">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-156">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-157">@No__t-0 元素設定為50圖元寬乘以70圖元高的大小，小於預設的版面配置設定。</span><span class="sxs-lookup"><span data-stu-id="80bcd-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="80bcd-158">@No__t-0 控制項的內容會據此重新排列。</span><span class="sxs-lookup"><span data-stu-id="80bcd-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="80bcd-159">設定版面配置屬性</span><span class="sxs-lookup"><span data-stu-id="80bcd-159">Setting Layout Properties</span></span>

<span data-ttu-id="80bcd-160">一律使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的屬性，在裝載的控制項上設定版面配置相關屬性。</span><span class="sxs-lookup"><span data-stu-id="80bcd-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="80bcd-161">直接在裝載的控制項上設定版面配置屬性，將產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="80bcd-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="80bcd-162">在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的裝載控制項上設定版面配置相關屬性沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="80bcd-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

<span data-ttu-id="80bcd-163">若要查看在裝載的控制項上設定屬性的效果，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-163">To see the effects of setting properties on the hosted control, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-164">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="80bcd-165">在**方案總管**中，按兩下 [ *mainwindow.xaml* ] 或 [ *MainWindow.xaml.cs* ]，在程式碼編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="80bcd-165">In **Solution Explorer**, double-click *MainWindow.xaml.vb* or *MainWindow.xaml.cs* to open it in the Code Editor.</span></span>

3. <span data-ttu-id="80bcd-166">將下列程式碼複製到 `MainWindow` 類別定義中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-166">Copy the following code into the `MainWindow` class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="80bcd-167">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-167">Press <kbd>F5</kbd> to build and run the application.</span></span>

5. <span data-ttu-id="80bcd-168">按一下 [**按一下我**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="80bcd-168">Click the **Click me** button.</span></span> <span data-ttu-id="80bcd-169">@No__t-0 事件處理常式會在裝載的控制項上設定 <xref:System.Windows.Forms.Control.Top%2A> 和 @no__t 2 屬性。</span><span class="sxs-lookup"><span data-stu-id="80bcd-169">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="80bcd-170">這會導致裝載的控制項重新置放在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素內。</span><span class="sxs-lookup"><span data-stu-id="80bcd-170">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="80bcd-171">主機會維持相同的螢幕區域，但會裁剪裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="80bcd-171">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="80bcd-172">相反地，裝載的控制項應一律填入 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素。</span><span class="sxs-lookup"><span data-stu-id="80bcd-172">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="80bcd-173">了解疊置順序的限制</span><span class="sxs-lookup"><span data-stu-id="80bcd-173">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="80bcd-174">可見 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素一律會在其他 WPF 專案上繪製，而且不會受到迭置順序的影響。</span><span class="sxs-lookup"><span data-stu-id="80bcd-174">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="80bcd-175">若要查看此迭置順序行為，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="80bcd-175">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="80bcd-176">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-176">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="80bcd-177">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-177">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-178">@No__t-0 元素會在 label 元素上繪製。</span><span class="sxs-lookup"><span data-stu-id="80bcd-178">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="80bcd-179">停駐</span><span class="sxs-lookup"><span data-stu-id="80bcd-179">Docking</span></span>

<span data-ttu-id="80bcd-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 銜接。</span><span class="sxs-lookup"><span data-stu-id="80bcd-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="80bcd-181">設定 @no__t 0 附加屬性，將裝載的控制項停駐在 @no__t 1 元素中。</span><span class="sxs-lookup"><span data-stu-id="80bcd-181">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

<span data-ttu-id="80bcd-182">若要停駐裝載的控制項，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-182">To dock a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-183">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-183">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="80bcd-184">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-184">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-185">@No__t-0 元素停駐在 <xref:System.Windows.Controls.DockPanel> 元素的右側。</span><span class="sxs-lookup"><span data-stu-id="80bcd-185">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="80bcd-186">設定可見度</span><span class="sxs-lookup"><span data-stu-id="80bcd-186">Setting Visibility</span></span>

<span data-ttu-id="80bcd-187">您可以在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素上設定 <xref:System.Windows.UIElement.Visibility%2A> 屬性，讓您的 @no__t 0 控制項不可見或折迭。</span><span class="sxs-lookup"><span data-stu-id="80bcd-187">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="80bcd-188">當控制項隱藏時，它不會顯示，但會佔據版面配置空間。</span><span class="sxs-lookup"><span data-stu-id="80bcd-188">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="80bcd-189">當控制項摺疊時，它不會顯示，也不會佔據配置空間。</span><span class="sxs-lookup"><span data-stu-id="80bcd-189">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

<span data-ttu-id="80bcd-190">若要設定裝載控制項的可見度，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-190">To set the visibility of a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-191">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-191">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="80bcd-192">在*mainwindow.xaml*或*MainWindow.xaml.cs*中，將下列程式碼複製到類別定義中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-192">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="80bcd-193">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-193">Press <kbd>F5</kbd> to build and run the application.</span></span>

4. <span data-ttu-id="80bcd-194">按一下 [**按一下以讓隱藏**專案] 按鈕，讓 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素不可見。</span><span class="sxs-lookup"><span data-stu-id="80bcd-194">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="80bcd-195">按一下 [**按一下以**折迭] 按鈕，以完全隱藏配置中的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素。</span><span class="sxs-lookup"><span data-stu-id="80bcd-195">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="80bcd-196">當 @no__t 0 控制項折迭時，周圍的元素會重新排列以佔用其空間。</span><span class="sxs-lookup"><span data-stu-id="80bcd-196">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="80bcd-197">裝載不會自動縮放的控制項</span><span class="sxs-lookup"><span data-stu-id="80bcd-197">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="80bcd-198">有些 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項具有固定的大小，且不會伸展以填滿配置中的可用空間。</span><span class="sxs-lookup"><span data-stu-id="80bcd-198">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="80bcd-199">例如，<xref:System.Windows.Forms.MonthCalendar> 控制項會在固定空間中顯示一個月。</span><span class="sxs-lookup"><span data-stu-id="80bcd-199">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

<span data-ttu-id="80bcd-200">若要裝載不會延展的控制項，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-200">To host a control that does not stretch, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-201">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-201">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="80bcd-202">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-202">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-203">@No__t-0 元素在方格資料列中置中，但不會伸展以填滿可用空間。</span><span class="sxs-lookup"><span data-stu-id="80bcd-203">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="80bcd-204">如果視窗夠大，您可能會看到兩個或多個月由主控的 <xref:System.Windows.Forms.MonthCalendar> 控制項顯示，但這些會在資料列中置中。</span><span class="sxs-lookup"><span data-stu-id="80bcd-204">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="80bcd-205">@No__t 0 版面配置引擎會將無法調整大小的元素置中，以填滿可用空間。</span><span class="sxs-lookup"><span data-stu-id="80bcd-205">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="80bcd-206">縮放</span><span class="sxs-lookup"><span data-stu-id="80bcd-206">Scaling</span></span>

<span data-ttu-id="80bcd-207">與 WPF 元素不同的是，大部分的 Windows Forms 控制項都不會持續擴充。</span><span class="sxs-lookup"><span data-stu-id="80bcd-207">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="80bcd-208">若要提供自訂調整，請覆寫 <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="80bcd-208">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="80bcd-209">若要使用預設行為來調整裝載的控制項，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-209">To scale a hosted control by using the default behavior, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-210">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-210">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="80bcd-211">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-211">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-212">裝載的控制項及其周圍元素會縮放 0.5 倍。</span><span class="sxs-lookup"><span data-stu-id="80bcd-212">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="80bcd-213">不過，裝載控制項的字型不會進行縮放。</span><span class="sxs-lookup"><span data-stu-id="80bcd-213">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="80bcd-214">旋轉</span><span class="sxs-lookup"><span data-stu-id="80bcd-214">Rotating</span></span>

<span data-ttu-id="80bcd-215">不同于 WPF 元素，Windows Forms 控制項不支援旋轉。</span><span class="sxs-lookup"><span data-stu-id="80bcd-215">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="80bcd-216">套用旋轉轉換時，@no__t 0 元素不會隨著其他 WPF 元素旋轉。</span><span class="sxs-lookup"><span data-stu-id="80bcd-216">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="80bcd-217">180度以外的任何旋轉值都會引發 <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> 事件。</span><span class="sxs-lookup"><span data-stu-id="80bcd-217">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

<span data-ttu-id="80bcd-218">若要查看在混合式應用程式中輪替的效果，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-218">To see the effect of rotation in a hybrid application, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-219">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-219">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="80bcd-220">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-220">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-221">裝載的控制項不會旋轉，但其周圍元素會旋轉 180 度。</span><span class="sxs-lookup"><span data-stu-id="80bcd-221">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="80bcd-222">您可能必須調整視窗大小來查看元素。</span><span class="sxs-lookup"><span data-stu-id="80bcd-222">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="80bcd-223">設定邊框距離及邊界</span><span class="sxs-lookup"><span data-stu-id="80bcd-223">Setting Padding and Margins</span></span>

<span data-ttu-id="80bcd-224">@No__t 0 版面配置中的填補和邊界，類似于 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中的填補和邊界。</span><span class="sxs-lookup"><span data-stu-id="80bcd-224">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="80bcd-225">只要在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素上設定 <xref:System.Windows.Controls.Control.Padding%2A> 和 @no__t 1 屬性即可。</span><span class="sxs-lookup"><span data-stu-id="80bcd-225">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

<span data-ttu-id="80bcd-226">若要設定主控控制項的填補和邊界，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-226">To set padding and margins for a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-227">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-227">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="80bcd-228">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-228">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-229">填補和邊界設定會以套用至 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 的相同方式套用至主控的 @no__t 0 控制項。</span><span class="sxs-lookup"><span data-stu-id="80bcd-229">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="80bcd-230">使用動態版面配置容器</span><span class="sxs-lookup"><span data-stu-id="80bcd-230">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="80bcd-231">提供兩個動態版面配置容器，<xref:System.Windows.Forms.FlowLayoutPanel> 和 @no__t 2。</span><span class="sxs-lookup"><span data-stu-id="80bcd-231">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="80bcd-232">您也可以在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置中使用這些容器。</span><span class="sxs-lookup"><span data-stu-id="80bcd-232">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

<span data-ttu-id="80bcd-233">若要使用動態版面配置容器，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="80bcd-233">To use a dynamic layout container, follow these steps:</span></span>

1. <span data-ttu-id="80bcd-234">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-234">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="80bcd-235">在*mainwindow.xaml*或*MainWindow.xaml.cs*中，將下列程式碼複製到類別定義中：</span><span class="sxs-lookup"><span data-stu-id="80bcd-235">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="80bcd-236">在函式中新增對 `InitializeFlowLayoutPanel` 方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="80bcd-236">Add a call to the `InitializeFlowLayoutPanel` method in the constructor:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="80bcd-237">按 <kbd>F5</kbd> 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80bcd-237">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="80bcd-238">@No__t-0 元素會填滿 <xref:System.Windows.Controls.DockPanel>，而 <xref:System.Windows.Forms.FlowLayoutPanel> 則會在預設的 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 中排列其子控制項。</span><span class="sxs-lookup"><span data-stu-id="80bcd-238">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="80bcd-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80bcd-239">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="80bcd-240">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="80bcd-240">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="80bcd-241">WindowsFormsHost 元素的配置考量</span><span class="sxs-lookup"><span data-stu-id="80bcd-241">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="80bcd-242">在 WPF 範例中排列 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="80bcd-242">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- <span data-ttu-id="80bcd-243">[逐步解說：在 WPF 中裝載 Windows Forms 複合控制項 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="80bcd-243">[Walkthrough: Hosting a Windows Forms Composite Control in WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)</span></span>
- <span data-ttu-id="80bcd-244">[逐步解說：在 Windows Forms @ no__t-0 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="80bcd-244">[Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)</span></span>
