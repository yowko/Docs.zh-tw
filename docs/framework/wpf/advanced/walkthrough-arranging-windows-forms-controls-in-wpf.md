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
ms.openlocfilehash: 5947168fabfe8ec22203029d9ec89b9719728413
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697617"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="a0b39-102">逐步解說：在 WPF 中排列 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="a0b39-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="a0b39-103">本逐步解說會示範如何使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置功能，來排列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]混合式應用程式中的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0b39-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="a0b39-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="a0b39-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a0b39-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="a0b39-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="a0b39-106">使用預設的版面配置設定。</span><span class="sxs-lookup"><span data-stu-id="a0b39-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="a0b39-107">依內容調整大小。</span><span class="sxs-lookup"><span data-stu-id="a0b39-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="a0b39-108">使用絕對位置。</span><span class="sxs-lookup"><span data-stu-id="a0b39-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="a0b39-109">明確指定大小。</span><span class="sxs-lookup"><span data-stu-id="a0b39-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="a0b39-110">設定版面配置屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b39-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="a0b39-111">了解疊置順序的限制。</span><span class="sxs-lookup"><span data-stu-id="a0b39-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="a0b39-112">停駐。</span><span class="sxs-lookup"><span data-stu-id="a0b39-112">Docking.</span></span>  
  
-   <span data-ttu-id="a0b39-113">設定可見度。</span><span class="sxs-lookup"><span data-stu-id="a0b39-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="a0b39-114">裝載不會自動縮放的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0b39-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="a0b39-115">縮放。</span><span class="sxs-lookup"><span data-stu-id="a0b39-115">Scaling.</span></span>  
  
-   <span data-ttu-id="a0b39-116">旋轉。</span><span class="sxs-lookup"><span data-stu-id="a0b39-116">Rotating.</span></span>  
  
-   <span data-ttu-id="a0b39-117">設定邊框距離及邊界。</span><span class="sxs-lookup"><span data-stu-id="a0b39-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="a0b39-118">使用動態版面配置容器。</span><span class="sxs-lookup"><span data-stu-id="a0b39-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="a0b39-119">在此逐步解說中所述工作的完整程式碼清單，請參閱 < [WPF 範例中排列 Windows Form 控制項](https://go.microsoft.com/fwlink/?LinkID=159971)。</span><span class="sxs-lookup"><span data-stu-id="a0b39-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="a0b39-120">當您完成時，您必須了解[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]版面配置功能在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a0b39-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="a0b39-121">Prerequisites</span></span>  

<span data-ttu-id="a0b39-122">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a0b39-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="creating-the-project"></a><span data-ttu-id="a0b39-123">建立專案</span><span class="sxs-lookup"><span data-stu-id="a0b39-123">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="a0b39-124">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="a0b39-124">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="a0b39-125">建立 WPF 應用程式專案，名為`WpfLayoutHostingWf`。</span><span class="sxs-lookup"><span data-stu-id="a0b39-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="a0b39-126">在 [方案總管] 中，加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="a0b39-126">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="a0b39-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="a0b39-127">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="a0b39-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="a0b39-128">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="a0b39-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="a0b39-129">System.Drawing</span></span>  
  
3.  <span data-ttu-id="a0b39-130">按兩下 MainWindow.xaml，在 XAML 檢視中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="a0b39-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="a0b39-131">在 <xref:System.Windows.Window>項目，新增下列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="a0b39-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="a0b39-132">在 <xref:System.Windows.Controls.Grid>項目集合<xref:System.Windows.Controls.Grid.ShowGridLines%2A>屬性設`true`和定義五個資料列和三個資料行。</span><span class="sxs-lookup"><span data-stu-id="a0b39-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="a0b39-133">使用預設的版面配置設定</span><span class="sxs-lookup"><span data-stu-id="a0b39-133">Using Default Layout Settings</span></span>  
 <span data-ttu-id="a0b39-134">根據預設，<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目處理所裝載的版面配置[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="a0b39-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="a0b39-135">使用預設的版面配置設定</span><span class="sxs-lookup"><span data-stu-id="a0b39-135">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="a0b39-136">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="a0b39-137">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-138">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType>控制項會出現在<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="a0b39-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="a0b39-139">裝載的控制項的大小調整，根據其內容，而<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會調整大小以容納裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0b39-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="a0b39-140">依內容調整大小</span><span class="sxs-lookup"><span data-stu-id="a0b39-140">Sizing to Content</span></span>  
 <span data-ttu-id="a0b39-141"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目可確保裝載的控制項調整大小，以正確顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="a0b39-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="a0b39-142">依內容調整大小</span><span class="sxs-lookup"><span data-stu-id="a0b39-142">To size to content</span></span>  
  
1.  <span data-ttu-id="a0b39-143">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="a0b39-144">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-145">兩個新的按鈕控制項的大小，以正確，顯示較長的文字字串和較大的字型大小和<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會調整大小以容納裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0b39-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="a0b39-146">使用絕對位置</span><span class="sxs-lookup"><span data-stu-id="a0b39-146">Using Absolute Positioning</span></span>  
 <span data-ttu-id="a0b39-147">您可以使用絕對位置放置<xref:System.Windows.Forms.Integration.WindowsFormsHost>使用者介面 (UI) 中的任何位置的項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="a0b39-148">使用絕對位置</span><span class="sxs-lookup"><span data-stu-id="a0b39-148">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="a0b39-149">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="a0b39-150">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目位於 20 像素為單位，從方格資料格上方和左邊的 20 個像素。</span><span class="sxs-lookup"><span data-stu-id="a0b39-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="a0b39-152">明確指定大小</span><span class="sxs-lookup"><span data-stu-id="a0b39-152">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="a0b39-153">您可以指定的大小<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目使用<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b39-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="a0b39-154">明確指定大小</span><span class="sxs-lookup"><span data-stu-id="a0b39-154">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="a0b39-155">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="a0b39-156">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-157"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目設定為大小為 50 像素寬 x 70 個像素高，這是小於預設版面配置設定。</span><span class="sxs-lookup"><span data-stu-id="a0b39-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="a0b39-158">內容[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]據以重新排列控制項。</span><span class="sxs-lookup"><span data-stu-id="a0b39-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="a0b39-159">設定版面配置屬性</span><span class="sxs-lookup"><span data-stu-id="a0b39-159">Setting Layout Properties</span></span>  
 <span data-ttu-id="a0b39-160">一律設定裝載控制項的配置相關的屬性所使用的屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="a0b39-161">直接在裝載的控制項上設定版面配置屬性，將產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="a0b39-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="a0b39-162">在裝載的控制項上設定版面配置相關屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="a0b39-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="a0b39-163">查看在裝載控制項上設定屬性的效果</span><span class="sxs-lookup"><span data-stu-id="a0b39-163">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="a0b39-164">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="a0b39-165">在 [方案總管] 中，按兩下 MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="a0b39-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="a0b39-166">vb 或 MainWindow.xaml.cs，以便在程式碼編輯器中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="a0b39-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="a0b39-167">下列程式碼複製到`MainWindow`類別定義。</span><span class="sxs-lookup"><span data-stu-id="a0b39-167">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4.  <span data-ttu-id="a0b39-168">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-168">Press F5 to build and run the application.</span></span>

5.  <span data-ttu-id="a0b39-169">按一下 [ **Click me** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a0b39-169">Click the **Click me** button.</span></span> <span data-ttu-id="a0b39-170">`button1_Click`事件處理常式集<xref:System.Windows.Forms.Control.Top%2A>和<xref:System.Windows.Forms.Control.Left%2A>上裝載的控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b39-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="a0b39-171">這會導致內重新置放裝載的控制項<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="a0b39-172">主機會維持相同的螢幕區域，但會裁剪裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="a0b39-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="a0b39-173">相反地，裝載的控制項一律應填滿<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="a0b39-174">了解疊置順序的限制</span><span class="sxs-lookup"><span data-stu-id="a0b39-174">Understanding Z-Order Limitations</span></span>
 <span data-ttu-id="a0b39-175">可見<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素一律應繪製之上其他 WPF 項目，以及它們不會受到疊置順序。</span><span class="sxs-lookup"><span data-stu-id="a0b39-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="a0b39-176">若要查看此疊置順序行為，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a0b39-176">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="a0b39-177">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2.  <span data-ttu-id="a0b39-178">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-179"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素已經繪製標籤項目上方。</span><span class="sxs-lookup"><span data-stu-id="a0b39-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>


## <a name="docking"></a><span data-ttu-id="a0b39-180">停駐</span><span class="sxs-lookup"><span data-stu-id="a0b39-180">Docking</span></span>
 <span data-ttu-id="a0b39-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]停駐。</span><span class="sxs-lookup"><span data-stu-id="a0b39-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="a0b39-182">設定<xref:System.Windows.Controls.DockPanel.Dock%2A>附加屬性，若要停駐中裝載的控制項<xref:System.Windows.Controls.DockPanel>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="a0b39-183">停駐裝載的控制項</span><span class="sxs-lookup"><span data-stu-id="a0b39-183">To dock a hosted control</span></span>

1.  <span data-ttu-id="a0b39-184">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2.  <span data-ttu-id="a0b39-185">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-186"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目停駐在右邊<xref:System.Windows.Controls.DockPanel>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="a0b39-187">設定可見度</span><span class="sxs-lookup"><span data-stu-id="a0b39-187">Setting Visibility</span></span>
 <span data-ttu-id="a0b39-188">您可以讓您[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項隱藏或摺疊它，藉由設定<xref:System.Windows.UIElement.Visibility%2A>屬性上的<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="a0b39-189">當控制項隱藏時，它不會顯示，但會佔據版面配置空間。</span><span class="sxs-lookup"><span data-stu-id="a0b39-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="a0b39-190">當控制項摺疊時，它不會顯示，也不會佔據配置空間。</span><span class="sxs-lookup"><span data-stu-id="a0b39-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="a0b39-191">設定裝載控制項的可見度</span><span class="sxs-lookup"><span data-stu-id="a0b39-191">To set the visibility of a hosted control</span></span>

1.  <span data-ttu-id="a0b39-192">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2.  <span data-ttu-id="a0b39-193">在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。</span><span class="sxs-lookup"><span data-stu-id="a0b39-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3.  <span data-ttu-id="a0b39-194">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-194">Press F5 to build and run the application.</span></span>

4.  <span data-ttu-id="a0b39-195">按一下 [**按一下即可隱藏**] 按鈕，使<xref:System.Windows.Forms.Integration.WindowsFormsHost>不可見的項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5.  <span data-ttu-id="a0b39-196">按一下 **按一下以摺疊**按鈕以隱藏<xref:System.Windows.Forms.Integration.WindowsFormsHost>從配置的項目完全。</span><span class="sxs-lookup"><span data-stu-id="a0b39-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="a0b39-197">當[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]摺疊控制項、 周圍的項目會重新排列，以佔用它的空間。</span><span class="sxs-lookup"><span data-stu-id="a0b39-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="a0b39-198">裝載不會自動縮放的控制項</span><span class="sxs-lookup"><span data-stu-id="a0b39-198">Hosting a Control That Does Not Stretch</span></span>
 <span data-ttu-id="a0b39-199">某些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項有固定的大小和執行自動縮放以填滿版面配置中的可用空間。</span><span class="sxs-lookup"><span data-stu-id="a0b39-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="a0b39-200">比方說，<xref:System.Windows.Forms.MonthCalendar>控制項固定間距來顯示月份。</span><span class="sxs-lookup"><span data-stu-id="a0b39-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="a0b39-201">裝載不會自動縮放的控制項</span><span class="sxs-lookup"><span data-stu-id="a0b39-201">To host a control that does not stretch</span></span>

1.  <span data-ttu-id="a0b39-202">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2.  <span data-ttu-id="a0b39-203">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-204"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會置於方格資料列，但它不會縮放以填滿可用空間。</span><span class="sxs-lookup"><span data-stu-id="a0b39-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="a0b39-205">如果視窗夠大，您可能會看到兩個或多個裝載所顯示的月份<xref:System.Windows.Forms.MonthCalendar>控制項，但這些是資料列中間。</span><span class="sxs-lookup"><span data-stu-id="a0b39-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="a0b39-206">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置引擎的中心無法調整大小以填滿可用空間的項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="a0b39-207">縮放</span><span class="sxs-lookup"><span data-stu-id="a0b39-207">Scaling</span></span>
 <span data-ttu-id="a0b39-208">不同於 WPF 項目，大部分的 Windows Form 控制項不會持續縮放。</span><span class="sxs-lookup"><span data-stu-id="a0b39-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="a0b39-209">若要提供自訂縮放比例，您覆寫<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="a0b39-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="a0b39-210">使用預設行為縮放裝載的控制項</span><span class="sxs-lookup"><span data-stu-id="a0b39-210">To scale a hosted control by using the default behavior</span></span>

1.  <span data-ttu-id="a0b39-211">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2.  <span data-ttu-id="a0b39-212">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-213">裝載的控制項及其周圍元素會縮放 0.5 倍。</span><span class="sxs-lookup"><span data-stu-id="a0b39-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="a0b39-214">不過，裝載控制項的字型不會進行縮放。</span><span class="sxs-lookup"><span data-stu-id="a0b39-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="a0b39-215">旋轉</span><span class="sxs-lookup"><span data-stu-id="a0b39-215">Rotating</span></span>
 <span data-ttu-id="a0b39-216">與 WPF 項目，不同的是 Windows Form 控制項不支援旋轉。</span><span class="sxs-lookup"><span data-stu-id="a0b39-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="a0b39-217"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目將不會與其他 WPF 項目套用旋轉轉換時才會旋轉。</span><span class="sxs-lookup"><span data-stu-id="a0b39-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="a0b39-218">180 度引發以外的任何旋轉值<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>事件。</span><span class="sxs-lookup"><span data-stu-id="a0b39-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="a0b39-219">查看混合式應用程式中的旋轉效果</span><span class="sxs-lookup"><span data-stu-id="a0b39-219">To see the effect of rotation in a hybrid application</span></span>

1.  <span data-ttu-id="a0b39-220">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2.  <span data-ttu-id="a0b39-221">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-222">裝載的控制項不會旋轉，但其周圍元素會旋轉 180 度。</span><span class="sxs-lookup"><span data-stu-id="a0b39-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="a0b39-223">您可能必須調整視窗大小來查看元素。</span><span class="sxs-lookup"><span data-stu-id="a0b39-223">You may have to resize the window to see the elements.</span></span>


## <a name="setting-padding-and-margins"></a><span data-ttu-id="a0b39-224">設定邊框距離及邊界</span><span class="sxs-lookup"><span data-stu-id="a0b39-224">Setting Padding and Margins</span></span>
 <span data-ttu-id="a0b39-225">邊框距離及邊界[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置是類似於邊框距離及邊界中的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a0b39-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="a0b39-226">只要設定<xref:System.Windows.Controls.Control.Padding%2A>並<xref:System.Windows.FrameworkElement.Margin%2A>上的屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="a0b39-227">設定裝載控制項的邊框距離及邊界</span><span class="sxs-lookup"><span data-stu-id="a0b39-227">To set padding and margins for a hosted control</span></span>

1.  <span data-ttu-id="a0b39-228">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2.  <span data-ttu-id="a0b39-229">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-230">邊框距離及邊界設定會套用到裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項中套用它們的方式相同[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a0b39-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="a0b39-231">使用動態版面配置容器</span><span class="sxs-lookup"><span data-stu-id="a0b39-231">Using Dynamic Layout Containers</span></span>
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="a0b39-232">提供兩個動態版面配置容器，<xref:System.Windows.Forms.FlowLayoutPanel>和<xref:System.Windows.Forms.TableLayoutPanel>。</span><span class="sxs-lookup"><span data-stu-id="a0b39-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="a0b39-233">您也可以使用這些容器中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置。</span><span class="sxs-lookup"><span data-stu-id="a0b39-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="a0b39-234">使用動態版面配置容器</span><span class="sxs-lookup"><span data-stu-id="a0b39-234">To use a dynamic layout container</span></span>

1.  <span data-ttu-id="a0b39-235">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="a0b39-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2.  <span data-ttu-id="a0b39-236">在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。</span><span class="sxs-lookup"><span data-stu-id="a0b39-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3.  <span data-ttu-id="a0b39-237">請在建構函式中加入 `InitializeFlowLayoutPanel` 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a0b39-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="a0b39-238">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b39-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="a0b39-239"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目填滿<xref:System.Windows.Controls.DockPanel>，並<xref:System.Windows.Forms.FlowLayoutPanel>排列它的子控制項，在預設<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>。</span><span class="sxs-lookup"><span data-stu-id="a0b39-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b39-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0b39-240">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a0b39-241">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="a0b39-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="a0b39-242">WindowsFormsHost 元素的配置考量</span><span class="sxs-lookup"><span data-stu-id="a0b39-242">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="a0b39-243">排列 Windows Form 控制項，在 WPF 範例</span><span class="sxs-lookup"><span data-stu-id="a0b39-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="a0b39-244">逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="a0b39-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="a0b39-245">逐步解說：裝載 Windows Forms 中的 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="a0b39-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
