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
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972300"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="704a4-102">逐步解說：在 WPF 中排列 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="704a4-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="704a4-103">本逐步解說將示範如何使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置功能, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]在混合式應用程式中排列控制項。</span><span class="sxs-lookup"><span data-stu-id="704a4-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="704a4-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="704a4-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="704a4-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="704a4-105">Creating the project.</span></span>

- <span data-ttu-id="704a4-106">使用預設的版面配置設定。</span><span class="sxs-lookup"><span data-stu-id="704a4-106">Using default layout settings.</span></span>

- <span data-ttu-id="704a4-107">依內容調整大小。</span><span class="sxs-lookup"><span data-stu-id="704a4-107">Sizing to content.</span></span>

- <span data-ttu-id="704a4-108">使用絕對位置。</span><span class="sxs-lookup"><span data-stu-id="704a4-108">Using absolute positioning.</span></span>

- <span data-ttu-id="704a4-109">明確指定大小。</span><span class="sxs-lookup"><span data-stu-id="704a4-109">Specifying size explicitly.</span></span>

- <span data-ttu-id="704a4-110">設定版面配置屬性。</span><span class="sxs-lookup"><span data-stu-id="704a4-110">Setting layout properties.</span></span>

- <span data-ttu-id="704a4-111">了解疊置順序的限制。</span><span class="sxs-lookup"><span data-stu-id="704a4-111">Understanding z-order limitations.</span></span>

- <span data-ttu-id="704a4-112">停駐。</span><span class="sxs-lookup"><span data-stu-id="704a4-112">Docking.</span></span>

- <span data-ttu-id="704a4-113">設定可見度。</span><span class="sxs-lookup"><span data-stu-id="704a4-113">Setting visibility.</span></span>

- <span data-ttu-id="704a4-114">裝載不會自動縮放的控制項。</span><span class="sxs-lookup"><span data-stu-id="704a4-114">Hosting a control that does not stretch.</span></span>

- <span data-ttu-id="704a4-115">縮放。</span><span class="sxs-lookup"><span data-stu-id="704a4-115">Scaling.</span></span>

- <span data-ttu-id="704a4-116">旋轉。</span><span class="sxs-lookup"><span data-stu-id="704a4-116">Rotating.</span></span>

- <span data-ttu-id="704a4-117">設定邊框距離及邊界。</span><span class="sxs-lookup"><span data-stu-id="704a4-117">Setting padding and margins.</span></span>

- <span data-ttu-id="704a4-118">使用動態版面配置容器。</span><span class="sxs-lookup"><span data-stu-id="704a4-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="704a4-119">如需本逐步解說中所述工作的完整程式代碼清單, 請參閱[在 WPF 中排列 Windows Forms 控制項範例](https://go.microsoft.com/fwlink/?LinkID=159971)。</span><span class="sxs-lookup"><span data-stu-id="704a4-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="704a4-120">當您完成時, 您將瞭解以[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式為基礎的版面配置功能。</span><span class="sxs-lookup"><span data-stu-id="704a4-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="704a4-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="704a4-121">Prerequisites</span></span>

<span data-ttu-id="704a4-122">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="704a4-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="704a4-123">建立專案</span><span class="sxs-lookup"><span data-stu-id="704a4-123">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="704a4-124">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="704a4-124">To create and set up the project</span></span>

1. <span data-ttu-id="704a4-125">建立名為`WpfLayoutHostingWf`的 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="704a4-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="704a4-126">在 [方案總管] 中，加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="704a4-126">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="704a4-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="704a4-127">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="704a4-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="704a4-128">System.Windows.Forms</span></span>

    - <span data-ttu-id="704a4-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="704a4-129">System.Drawing</span></span>

3. <span data-ttu-id="704a4-130">按兩下 MainWindow.xaml，在 XAML 檢視中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="704a4-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>

4. <span data-ttu-id="704a4-131">在元素中, 新增下列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命名空間對應。 <xref:System.Windows.Window></span><span class="sxs-lookup"><span data-stu-id="704a4-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="704a4-132">在元素中, <xref:System.Windows.Controls.Grid.ShowGridLines%2A>將屬性設定`true`為, 並定義五個數據列和三個數據行。 <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="704a4-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="704a4-133">使用預設的版面配置設定</span><span class="sxs-lookup"><span data-stu-id="704a4-133">Using Default Layout Settings</span></span>

<span data-ttu-id="704a4-134">根據預設, <xref:System.Windows.Forms.Integration.WindowsFormsHost>專案會處理裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項的版面配置。</span><span class="sxs-lookup"><span data-stu-id="704a4-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-use-default-layout-settings"></a><span data-ttu-id="704a4-135">使用預設的版面配置設定</span><span class="sxs-lookup"><span data-stu-id="704a4-135">To use default layout settings</span></span>

1. <span data-ttu-id="704a4-136">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="704a4-137">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-138">控制項會出現在中<xref:System.Windows.Controls.Canvas>。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="704a4-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="704a4-139">裝載的控制項會根據其內容調整大小, 而元素<xref:System.Windows.Forms.Integration.WindowsFormsHost>的大小則會調整以容納裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="704a4-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="704a4-140">依內容調整大小</span><span class="sxs-lookup"><span data-stu-id="704a4-140">Sizing to Content</span></span>

<span data-ttu-id="704a4-141"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素可確保裝載的控制項已調整大小, 以適當地顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="704a4-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

### <a name="to-size-to-content"></a><span data-ttu-id="704a4-142">依內容調整大小</span><span class="sxs-lookup"><span data-stu-id="704a4-142">To size to content</span></span>

1. <span data-ttu-id="704a4-143">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="704a4-144">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-145">這兩個新的按鈕控制項會調整大小, 以適當地顯示較長的文字字串和<xref:System.Windows.Forms.Integration.WindowsFormsHost>較大的字型大小, 並調整專案大小以配合裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="704a4-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="704a4-146">使用絕對位置</span><span class="sxs-lookup"><span data-stu-id="704a4-146">Using Absolute Positioning</span></span>

<span data-ttu-id="704a4-147">您可以使用絕對位置, 將<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素放在使用者介面 (UI) 的任何位置。</span><span class="sxs-lookup"><span data-stu-id="704a4-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

### <a name="to-use-absolute-positioning"></a><span data-ttu-id="704a4-148">使用絕對位置</span><span class="sxs-lookup"><span data-stu-id="704a4-148">To use absolute positioning</span></span>

1. <span data-ttu-id="704a4-149">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="704a4-150">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會從方格資料格的頂端放置20個圖元, 而從左邊起算20個圖元。</span><span class="sxs-lookup"><span data-stu-id="704a4-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="704a4-152">明確指定大小</span><span class="sxs-lookup"><span data-stu-id="704a4-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="704a4-153">您可以<xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.FrameworkElement.Width%2A>使用和<xref:System.Windows.FrameworkElement.Height%2A>屬性來指定元素的大小。</span><span class="sxs-lookup"><span data-stu-id="704a4-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

### <a name="to-specify-size-explicitly"></a><span data-ttu-id="704a4-154">明確指定大小</span><span class="sxs-lookup"><span data-stu-id="704a4-154">To specify size explicitly</span></span>

1. <span data-ttu-id="704a4-155">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="704a4-156">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-157"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素設定為50圖元寬乘以70圖元高的大小, 小於預設的版面配置設定。</span><span class="sxs-lookup"><span data-stu-id="704a4-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="704a4-158">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項的內容會據以重新排列。</span><span class="sxs-lookup"><span data-stu-id="704a4-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="704a4-159">設定版面配置屬性</span><span class="sxs-lookup"><span data-stu-id="704a4-159">Setting Layout Properties</span></span>

<span data-ttu-id="704a4-160">一律使用<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的屬性, 在裝載的控制項上設定版面配置相關屬性。</span><span class="sxs-lookup"><span data-stu-id="704a4-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="704a4-161">直接在裝載的控制項上設定版面配置屬性，將產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="704a4-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="704a4-162">在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的裝載控制項上設定版面配置相關屬性沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="704a4-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="704a4-163">查看在裝載控制項上設定屬性的效果</span><span class="sxs-lookup"><span data-stu-id="704a4-163">To see the effects of setting properties on the hosted control</span></span>

1. <span data-ttu-id="704a4-164">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="704a4-165">在 [方案總管] 中，按兩下 MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="704a4-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="704a4-166">vb 或 MainWindow.xaml.cs，以便在程式碼編輯器中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="704a4-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>

3. <span data-ttu-id="704a4-167">將下列程式碼複製到`MainWindow`類別定義中。</span><span class="sxs-lookup"><span data-stu-id="704a4-167">Copy the following code into the `MainWindow` class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="704a4-168">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-168">Press F5 to build and run the application.</span></span>

5. <span data-ttu-id="704a4-169">按一下 [**按一下我**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="704a4-169">Click the **Click me** button.</span></span> <span data-ttu-id="704a4-170">事件處理常式會在<xref:System.Windows.Forms.Control.Top%2A>裝載<xref:System.Windows.Forms.Control.Left%2A>的控制項上設定和屬性。 `button1_Click`</span><span class="sxs-lookup"><span data-stu-id="704a4-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="704a4-171">這會導致裝載的控制項重新置放在<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素內。</span><span class="sxs-lookup"><span data-stu-id="704a4-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="704a4-172">主機會維持相同的螢幕區域，但會裁剪裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="704a4-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="704a4-173">相反地, 裝載的控制項應一律填<xref:System.Windows.Forms.Integration.WindowsFormsHost>滿元素。</span><span class="sxs-lookup"><span data-stu-id="704a4-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="704a4-174">了解疊置順序的限制</span><span class="sxs-lookup"><span data-stu-id="704a4-174">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="704a4-175">可見<xref:System.Windows.Forms.Integration.WindowsFormsHost>的元素一律會在其他 WPF 專案上繪製, 而且不會受到迭置順序的影響。</span><span class="sxs-lookup"><span data-stu-id="704a4-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="704a4-176">若要查看此迭置順序行為, 請執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="704a4-176">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="704a4-177">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="704a4-178">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-179"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會在 label 元素上繪製。</span><span class="sxs-lookup"><span data-stu-id="704a4-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="704a4-180">停駐</span><span class="sxs-lookup"><span data-stu-id="704a4-180">Docking</span></span>

<span data-ttu-id="704a4-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]停駐。</span><span class="sxs-lookup"><span data-stu-id="704a4-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="704a4-182">設定附加屬性, 將裝載的控制項停駐于<xref:System.Windows.Controls.DockPanel>元素中。 <xref:System.Windows.Controls.DockPanel.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="704a4-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="704a4-183">停駐裝載的控制項</span><span class="sxs-lookup"><span data-stu-id="704a4-183">To dock a hosted control</span></span>

1. <span data-ttu-id="704a4-184">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="704a4-185">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-186">元素會停駐在專案的右側<xref:System.Windows.Controls.DockPanel>。 <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="704a4-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="704a4-187">設定可見度</span><span class="sxs-lookup"><span data-stu-id="704a4-187">Setting Visibility</span></span>

<span data-ttu-id="704a4-188">您可以藉由[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]設定專案上<xref:System.Windows.Forms.Integration.WindowsFormsHost>的<xref:System.Windows.UIElement.Visibility%2A>屬性, 讓控制項不可見或折迭。</span><span class="sxs-lookup"><span data-stu-id="704a4-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="704a4-189">當控制項隱藏時，它不會顯示，但會佔據版面配置空間。</span><span class="sxs-lookup"><span data-stu-id="704a4-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="704a4-190">當控制項摺疊時，它不會顯示，也不會佔據配置空間。</span><span class="sxs-lookup"><span data-stu-id="704a4-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="704a4-191">設定裝載控制項的可見度</span><span class="sxs-lookup"><span data-stu-id="704a4-191">To set the visibility of a hosted control</span></span>

1. <span data-ttu-id="704a4-192">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="704a4-193">在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。</span><span class="sxs-lookup"><span data-stu-id="704a4-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="704a4-194">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-194">Press F5 to build and run the application.</span></span>

4. <span data-ttu-id="704a4-195">按一下 [**按一下以讓隱藏**專案] 按鈕, <xref:System.Windows.Forms.Integration.WindowsFormsHost>讓元素看不見。</span><span class="sxs-lookup"><span data-stu-id="704a4-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="704a4-196">按一下 [**按一下以**折迭] 按鈕, <xref:System.Windows.Forms.Integration.WindowsFormsHost>以完全隱藏版面配置中的元素。</span><span class="sxs-lookup"><span data-stu-id="704a4-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="704a4-197">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]當控制項折迭時, 周圍的元素會重新排列以佔用其空間。</span><span class="sxs-lookup"><span data-stu-id="704a4-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="704a4-198">裝載不會自動縮放的控制項</span><span class="sxs-lookup"><span data-stu-id="704a4-198">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="704a4-199">有些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項具有固定的大小, 且不會伸展以填滿配置中的可用空間。</span><span class="sxs-lookup"><span data-stu-id="704a4-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="704a4-200">例如, <xref:System.Windows.Forms.MonthCalendar>控制項會在固定空間中顯示一個月。</span><span class="sxs-lookup"><span data-stu-id="704a4-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="704a4-201">裝載不會自動縮放的控制項</span><span class="sxs-lookup"><span data-stu-id="704a4-201">To host a control that does not stretch</span></span>

1. <span data-ttu-id="704a4-202">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="704a4-203">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-204"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會置中在方格的資料列中, 但不會伸展以填滿可用的空間。</span><span class="sxs-lookup"><span data-stu-id="704a4-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="704a4-205">如果視窗夠大, 您可能會看到兩個以上的月份是由<xref:System.Windows.Forms.MonthCalendar>裝載的控制項所顯示, 但這些是以資料列為中心。</span><span class="sxs-lookup"><span data-stu-id="704a4-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="704a4-206">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置引擎會將無法調整大小的元素置中, 以填滿可用空間。</span><span class="sxs-lookup"><span data-stu-id="704a4-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="704a4-207">縮放</span><span class="sxs-lookup"><span data-stu-id="704a4-207">Scaling</span></span>

<span data-ttu-id="704a4-208">與 WPF 元素不同的是, 大部分的 Windows Forms 控制項都不會持續擴充。</span><span class="sxs-lookup"><span data-stu-id="704a4-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="704a4-209">若要提供自訂調整, 請<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="704a4-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="704a4-210">使用預設行為縮放裝載的控制項</span><span class="sxs-lookup"><span data-stu-id="704a4-210">To scale a hosted control by using the default behavior</span></span>

1. <span data-ttu-id="704a4-211">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="704a4-212">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-213">裝載的控制項及其周圍元素會縮放 0.5 倍。</span><span class="sxs-lookup"><span data-stu-id="704a4-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="704a4-214">不過，裝載控制項的字型不會進行縮放。</span><span class="sxs-lookup"><span data-stu-id="704a4-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="704a4-215">旋轉</span><span class="sxs-lookup"><span data-stu-id="704a4-215">Rotating</span></span>

<span data-ttu-id="704a4-216">不同于 WPF 元素, Windows Forms 控制項不支援旋轉。</span><span class="sxs-lookup"><span data-stu-id="704a4-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="704a4-217">套用<xref:System.Windows.Forms.Integration.WindowsFormsHost>旋轉轉換時, 元素不會與其他 WPF 專案一起旋轉。</span><span class="sxs-lookup"><span data-stu-id="704a4-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="704a4-218">180度以外的<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>任何旋轉值都會引發事件。</span><span class="sxs-lookup"><span data-stu-id="704a4-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="704a4-219">查看混合式應用程式中的旋轉效果</span><span class="sxs-lookup"><span data-stu-id="704a4-219">To see the effect of rotation in a hybrid application</span></span>

1. <span data-ttu-id="704a4-220">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="704a4-221">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-222">裝載的控制項不會旋轉，但其周圍元素會旋轉 180 度。</span><span class="sxs-lookup"><span data-stu-id="704a4-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="704a4-223">您可能必須調整視窗大小來查看元素。</span><span class="sxs-lookup"><span data-stu-id="704a4-223">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="704a4-224">設定邊框距離及邊界</span><span class="sxs-lookup"><span data-stu-id="704a4-224">Setting Padding and Margins</span></span>

<span data-ttu-id="704a4-225">版面配置中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的填補和邊界類似于中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]的填補和邊界。</span><span class="sxs-lookup"><span data-stu-id="704a4-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="704a4-226">只要在<xref:System.Windows.Controls.Control.Padding%2A> 元素<xref:System.Windows.Forms.Integration.WindowsFormsHost>上<xref:System.Windows.FrameworkElement.Margin%2A>設定和屬性即可。</span><span class="sxs-lookup"><span data-stu-id="704a4-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="704a4-227">設定裝載控制項的邊框距離及邊界</span><span class="sxs-lookup"><span data-stu-id="704a4-227">To set padding and margins for a hosted control</span></span>

1. <span data-ttu-id="704a4-228">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="704a4-229">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-230">填補和邊界設定會以套用它們[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]的相同方式套用至裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="704a4-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="704a4-231">使用動態版面配置容器</span><span class="sxs-lookup"><span data-stu-id="704a4-231">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="704a4-232">提供兩個動態版面配置<xref:System.Windows.Forms.FlowLayoutPanel>容器<xref:System.Windows.Forms.TableLayoutPanel>: 和。</span><span class="sxs-lookup"><span data-stu-id="704a4-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="704a4-233">您也可以在版面配置中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用這些容器。</span><span class="sxs-lookup"><span data-stu-id="704a4-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="704a4-234">使用動態版面配置容器</span><span class="sxs-lookup"><span data-stu-id="704a4-234">To use a dynamic layout container</span></span>

1. <span data-ttu-id="704a4-235">將下列 XAML 複製到<xref:System.Windows.Controls.Grid>元素中。</span><span class="sxs-lookup"><span data-stu-id="704a4-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="704a4-236">在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。</span><span class="sxs-lookup"><span data-stu-id="704a4-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="704a4-237">請在建構函式中加入 `InitializeFlowLayoutPanel` 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="704a4-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="704a4-238">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="704a4-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="704a4-239">元素會<xref:System.Windows.Forms.FlowLayoutPanel>填滿<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>, 並在預設值中排列其子控制項。 <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="704a4-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="704a4-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="704a4-240">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="704a4-241">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="704a4-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="704a4-242">WindowsFormsHost 元素的配置考量</span><span class="sxs-lookup"><span data-stu-id="704a4-242">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="704a4-243">在 WPF 範例中排列 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="704a4-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="704a4-244">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="704a4-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="704a4-245">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="704a4-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
