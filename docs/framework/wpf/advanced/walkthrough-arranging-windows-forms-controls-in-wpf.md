---
title: 逐步解說：在 WPF 中排列 Windows Form 控制項
ms.custom: ''
ms.date: 04/03/2018
ms.prod: .net-framework
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3129b4128444530b1277299f3f95ce49232421
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="188f6-102">逐步解說：在 WPF 中排列 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="188f6-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="188f6-103">本逐步解說會示範如何使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置功能來排列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]混合式應用程式中的控制項。</span><span class="sxs-lookup"><span data-stu-id="188f6-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="188f6-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="188f6-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="188f6-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="188f6-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="188f6-106">使用預設的版面配置設定。</span><span class="sxs-lookup"><span data-stu-id="188f6-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="188f6-107">依內容調整大小。</span><span class="sxs-lookup"><span data-stu-id="188f6-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="188f6-108">使用絕對位置。</span><span class="sxs-lookup"><span data-stu-id="188f6-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="188f6-109">明確指定大小。</span><span class="sxs-lookup"><span data-stu-id="188f6-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="188f6-110">設定版面配置屬性。</span><span class="sxs-lookup"><span data-stu-id="188f6-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="188f6-111">了解疊置順序的限制。</span><span class="sxs-lookup"><span data-stu-id="188f6-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="188f6-112">停駐。</span><span class="sxs-lookup"><span data-stu-id="188f6-112">Docking.</span></span>  
  
-   <span data-ttu-id="188f6-113">設定可見度。</span><span class="sxs-lookup"><span data-stu-id="188f6-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="188f6-114">裝載不會自動縮放的控制項。</span><span class="sxs-lookup"><span data-stu-id="188f6-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="188f6-115">縮放。</span><span class="sxs-lookup"><span data-stu-id="188f6-115">Scaling.</span></span>  
  
-   <span data-ttu-id="188f6-116">旋轉。</span><span class="sxs-lookup"><span data-stu-id="188f6-116">Rotating.</span></span>  
  
-   <span data-ttu-id="188f6-117">設定邊框距離及邊界。</span><span class="sxs-lookup"><span data-stu-id="188f6-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="188f6-118">使用動態版面配置容器。</span><span class="sxs-lookup"><span data-stu-id="188f6-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="188f6-119">在此逐步解說中所述的工作的完整程式碼清單，請參閱[排列 Windows Form 控制項中 WPF 範例](http://go.microsoft.com/fwlink/?LinkID=159971)。</span><span class="sxs-lookup"><span data-stu-id="188f6-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="188f6-120">當您完成時，您必須了解[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]版面配置中的功能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="188f6-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="188f6-121">Prerequisites</span></span>  
 <span data-ttu-id="188f6-122">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="188f6-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="188f6-123">.</span><span class="sxs-lookup"><span data-stu-id="188f6-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="188f6-124">建立專案</span><span class="sxs-lookup"><span data-stu-id="188f6-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="188f6-125">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="188f6-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="188f6-126">建立 WPF 應用程式專案，名為`WpfLayoutHostingWf`。</span><span class="sxs-lookup"><span data-stu-id="188f6-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="188f6-127">在 [方案總管] 中，加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="188f6-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="188f6-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="188f6-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="188f6-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="188f6-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="188f6-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="188f6-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="188f6-131">按兩下 MainWindow.xaml，在 XAML 檢視中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="188f6-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="188f6-132">在<xref:System.Windows.Window>項目，加入下列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="188f6-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="188f6-133">在<xref:System.Windows.Controls.Grid>項目集合<xref:System.Windows.Controls.Grid.ShowGridLines%2A>屬性`true`和定義五個資料列和三個資料行。</span><span class="sxs-lookup"><span data-stu-id="188f6-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="188f6-134">使用預設的版面配置設定</span><span class="sxs-lookup"><span data-stu-id="188f6-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="188f6-135">根據預設，<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會處理裝載的版面配置[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="188f6-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="188f6-136">使用預設的版面配置設定</span><span class="sxs-lookup"><span data-stu-id="188f6-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="188f6-137">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="188f6-138">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType>控制項出現在<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="188f6-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="188f6-140">裝載的控制項的大小調整為根據其內容，而<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會調整成足以容納裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="188f6-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="188f6-141">依內容調整大小</span><span class="sxs-lookup"><span data-stu-id="188f6-141">Sizing to Content</span></span>  
 <span data-ttu-id="188f6-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素可確保裝載的控制項的大小來正確顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="188f6-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="188f6-143">依內容調整大小</span><span class="sxs-lookup"><span data-stu-id="188f6-143">To size to content</span></span>  
  
1.  <span data-ttu-id="188f6-144">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="188f6-145">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-146">兩個新的按鈕控制項的大小，以顯示較長的文字字串和大字型大小正常運作，而<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會調整大小以容納裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="188f6-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="188f6-147">使用絕對位置</span><span class="sxs-lookup"><span data-stu-id="188f6-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="188f6-148">您可以使用絕對位置放置<xref:System.Windows.Forms.Integration.WindowsFormsHost>使用者介面 (UI) 中的任何位置的項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="188f6-149">使用絕對位置</span><span class="sxs-lookup"><span data-stu-id="188f6-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="188f6-150">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="188f6-151">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會放 20 像素為單位，從方格資料格的頂端和左側 20 像素為單位。</span><span class="sxs-lookup"><span data-stu-id="188f6-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="188f6-153">明確指定大小</span><span class="sxs-lookup"><span data-stu-id="188f6-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="188f6-154">您可以指定的大小<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目使用<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="188f6-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="188f6-155">明確指定大小</span><span class="sxs-lookup"><span data-stu-id="188f6-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="188f6-156">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="188f6-157">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素設定為大小為 50 像素寬 x 70 像素高，其小於預設版面配置設定。</span><span class="sxs-lookup"><span data-stu-id="188f6-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="188f6-159">內容[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]據以重新排列控制項。</span><span class="sxs-lookup"><span data-stu-id="188f6-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="188f6-160">設定版面配置屬性</span><span class="sxs-lookup"><span data-stu-id="188f6-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="188f6-161">一律與配置有關的屬性上設定裝載控制項使用之屬性的<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="188f6-162">直接在裝載的控制項上設定版面配置屬性，將產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="188f6-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="188f6-163">在裝載控制項上設定與配置有關的屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="188f6-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="188f6-164">查看在裝載控制項上設定屬性的效果</span><span class="sxs-lookup"><span data-stu-id="188f6-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="188f6-165">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="188f6-166">在 [方案總管] 中，按兩下 MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="188f6-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="188f6-167">vb 或 MainWindow.xaml.cs，以便在程式碼編輯器中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="188f6-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="188f6-168">下列程式碼複製到`MainWindow`類別定義。</span><span class="sxs-lookup"><span data-stu-id="188f6-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="188f6-169">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="188f6-170">按一下**Click me**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="188f6-170">Click the **Click me** button.</span></span> <span data-ttu-id="188f6-171">`button1_Click`事件處理常式設定<xref:System.Windows.Forms.Control.Top%2A>和<xref:System.Windows.Forms.Control.Left%2A>裝載控制項上的屬性。</span><span class="sxs-lookup"><span data-stu-id="188f6-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="188f6-172">這會造成裝載的控制項內重新定位<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="188f6-173">主機會維持相同的螢幕區域，但會裁剪裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="188f6-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="188f6-174">相反地，在裝載的控制項應該永遠填滿<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="188f6-175">了解疊置順序的限制</span><span class="sxs-lookup"><span data-stu-id="188f6-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="188f6-176">可見<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會永遠繪製之上其他 WPF 項目，而且它們可依 z 軸順序不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="188f6-176">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="188f6-177">若要查看此疊置順序的行為，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="188f6-177">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="188f6-178">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-178">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  <span data-ttu-id="188f6-179">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-179">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素已經繪製在標籤項目上方。</span><span class="sxs-lookup"><span data-stu-id="188f6-180">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  


## <a name="docking"></a><span data-ttu-id="188f6-181">停駐</span><span class="sxs-lookup"><span data-stu-id="188f6-181">Docking</span></span>  
 <span data-ttu-id="188f6-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]停駐。</span><span class="sxs-lookup"><span data-stu-id="188f6-182"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="188f6-183">設定<xref:System.Windows.Controls.DockPanel.Dock%2A>附加停駐在裝載的控制項的屬性<xref:System.Windows.Controls.DockPanel>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-183">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="188f6-184">停駐裝載的控制項</span><span class="sxs-lookup"><span data-stu-id="188f6-184">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="188f6-185">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-185">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="188f6-186">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-186">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost>元素停駐在右邊的 list<xref:System.Windows.Controls.DockPanel>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-187">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="188f6-188">設定可見度</span><span class="sxs-lookup"><span data-stu-id="188f6-188">Setting Visibility</span></span>  
 <span data-ttu-id="188f6-189">您可以讓您[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制隱藏或摺疊它，藉由設定<xref:System.Windows.UIElement.Visibility%2A>屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-189">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="188f6-190">當控制項隱藏時，它不會顯示，但會佔據版面配置空間。</span><span class="sxs-lookup"><span data-stu-id="188f6-190">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="188f6-191">當控制項摺疊時，它不會顯示，也不會佔據配置空間。</span><span class="sxs-lookup"><span data-stu-id="188f6-191">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="188f6-192">設定裝載控制項的可見度</span><span class="sxs-lookup"><span data-stu-id="188f6-192">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="188f6-193">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-193">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="188f6-194">在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。</span><span class="sxs-lookup"><span data-stu-id="188f6-194">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="188f6-195">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-195">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="188f6-196">按一下**按一下讓看不到** 按鈕，使<xref:System.Windows.Forms.Integration.WindowsFormsHost>不可見的項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-196">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="188f6-197">按一下**按一下以摺疊**按鈕隱藏<xref:System.Windows.Forms.Integration.WindowsFormsHost>版面配置中的項目完全。</span><span class="sxs-lookup"><span data-stu-id="188f6-197">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="188f6-198">當[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項摺疊、 周圍的項目就會重新排列，以佔用的空間。</span><span class="sxs-lookup"><span data-stu-id="188f6-198">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="188f6-199">裝載不會自動縮放的控制項</span><span class="sxs-lookup"><span data-stu-id="188f6-199">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="188f6-200">某些[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項有固定的大小和執行自動縮放以填滿配置中的可用空間。</span><span class="sxs-lookup"><span data-stu-id="188f6-200">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="188f6-201">例如，<xref:System.Windows.Forms.MonthCalendar>控制項會顯示每個月固定間距。</span><span class="sxs-lookup"><span data-stu-id="188f6-201">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="188f6-202">裝載不會自動縮放的控制項</span><span class="sxs-lookup"><span data-stu-id="188f6-202">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="188f6-203">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-203">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="188f6-204">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-204">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-205"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目置於格線資料列，但它不會延伸以填滿可用空間。</span><span class="sxs-lookup"><span data-stu-id="188f6-205">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="188f6-206">如果視窗是夠大，您可能會看到兩個或多個月，顯示託管<xref:System.Windows.Forms.MonthCalendar>控制項，但這些置中對齊的資料列中。</span><span class="sxs-lookup"><span data-stu-id="188f6-206">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="188f6-207">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置引擎中心無法調整大小以填滿可用空間的項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-207">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="188f6-208">縮放</span><span class="sxs-lookup"><span data-stu-id="188f6-208">Scaling</span></span>  
 <span data-ttu-id="188f6-209">不同於 WPF 項目，大部分的 Windows Form 控制項不會持續擴充。</span><span class="sxs-lookup"><span data-stu-id="188f6-209">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="188f6-210">若要提供自訂縮放比例，您覆寫<xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="188f6-210">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span> 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="188f6-211">使用預設行為縮放裝載的控制項</span><span class="sxs-lookup"><span data-stu-id="188f6-211">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="188f6-212">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-212">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="188f6-213">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-213">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-214">裝載的控制項及其周圍元素會縮放 0.5 倍。</span><span class="sxs-lookup"><span data-stu-id="188f6-214">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="188f6-215">不過，裝載控制項的字型不會進行縮放。</span><span class="sxs-lookup"><span data-stu-id="188f6-215">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="188f6-216">旋轉</span><span class="sxs-lookup"><span data-stu-id="188f6-216">Rotating</span></span>  
 <span data-ttu-id="188f6-217">不同於 WPF 項目，Windows Form 控制項不支援循環。</span><span class="sxs-lookup"><span data-stu-id="188f6-217">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="188f6-218"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目將不會與其他 WPF 項目套用旋轉轉換時才會旋轉。</span><span class="sxs-lookup"><span data-stu-id="188f6-218">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="188f6-219">任何旋轉以外值 180 度引發<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>事件。</span><span class="sxs-lookup"><span data-stu-id="188f6-219">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="188f6-220">查看混合式應用程式中的旋轉效果</span><span class="sxs-lookup"><span data-stu-id="188f6-220">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="188f6-221">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-221">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="188f6-222">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-222">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-223">裝載的控制項不會旋轉，但其周圍元素會旋轉 180 度。</span><span class="sxs-lookup"><span data-stu-id="188f6-223">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="188f6-224">您可能必須調整視窗大小來查看元素。</span><span class="sxs-lookup"><span data-stu-id="188f6-224">You may have to resize the window to see the elements.</span></span>  
 

## <a name="setting-padding-and-margins"></a><span data-ttu-id="188f6-225">設定邊框距離及邊界</span><span class="sxs-lookup"><span data-stu-id="188f6-225">Setting Padding and Margins</span></span>  
 <span data-ttu-id="188f6-226">填補和邊界[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置，類似填補和邊界[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="188f6-226">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="188f6-227">只要設定<xref:System.Windows.Controls.Control.Padding%2A>和<xref:System.Windows.FrameworkElement.Margin%2A>屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-227">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="188f6-228">設定裝載控制項的邊框距離及邊界</span><span class="sxs-lookup"><span data-stu-id="188f6-228">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="188f6-229">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-229">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="188f6-230">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-230">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-231">填補和邊界設定會套用至主控[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項相同的方式會將它們套用在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="188f6-231">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="188f6-232">使用動態版面配置容器</span><span class="sxs-lookup"><span data-stu-id="188f6-232">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="188f6-233"> 提供兩個動態的版面配置容器，<xref:System.Windows.Forms.FlowLayoutPanel>和<xref:System.Windows.Forms.TableLayoutPanel>。</span><span class="sxs-lookup"><span data-stu-id="188f6-233"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="188f6-234">您也可以使用這些容器中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版面配置。</span><span class="sxs-lookup"><span data-stu-id="188f6-234">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="188f6-235">使用動態版面配置容器</span><span class="sxs-lookup"><span data-stu-id="188f6-235">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="188f6-236">複製成下列 XAML<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="188f6-236">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="188f6-237">在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼複製到類別定義中。</span><span class="sxs-lookup"><span data-stu-id="188f6-237">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="188f6-238">將呼叫加入`InitializeFlowLayoutPanel`建構函式中的方法。</span><span class="sxs-lookup"><span data-stu-id="188f6-238">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="188f6-239">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="188f6-239">Press F5 to build and run the application.</span></span> <span data-ttu-id="188f6-240"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目都會填入<xref:System.Windows.Controls.DockPanel>，和<xref:System.Windows.Forms.FlowLayoutPanel>排列其子控制項中的預設<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>。</span><span class="sxs-lookup"><span data-stu-id="188f6-240">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="188f6-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="188f6-241">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="188f6-242">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="188f6-242">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="188f6-243">WindowsFormsHost 元素的配置考量</span><span class="sxs-lookup"><span data-stu-id="188f6-243">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="188f6-244">排列 Windows Form 控制項中的 WPF 範例</span><span class="sxs-lookup"><span data-stu-id="188f6-244">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="188f6-245">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="188f6-245">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="188f6-246">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="188f6-246">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
