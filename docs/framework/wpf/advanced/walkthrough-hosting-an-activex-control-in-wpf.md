---
title: 逐步解說：將 ActiveX 控制項裝載在 WPF 中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 0181093de1c40889110ab7eae75a3847a17845a9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859942"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="785a3-102">逐步解說：將 ActiveX 控制項裝載在 WPF 中</span><span class="sxs-lookup"><span data-stu-id="785a3-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="785a3-103">若要啟用改善的瀏覽器互動，您可以使用 Microsoft ActiveX 控制項，在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="785a3-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="785a3-104">本逐步解說示範您可以託管[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]上的控制項為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="785a3-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="785a3-105">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="785a3-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="785a3-106">建立專案。</span><span class="sxs-lookup"><span data-stu-id="785a3-106">Creating the project.</span></span>

- <span data-ttu-id="785a3-107">建立 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="785a3-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="785a3-108">裝載 WPF 頁面上的 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="785a3-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="785a3-109">當您完成這個逐步解說中時，您將了解如何使用 Microsoft ActiveX 控制項，在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="785a3-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="785a3-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="785a3-110">Prerequisites</span></span>
 <span data-ttu-id="785a3-111">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="785a3-111">You need the following components to complete this walkthrough:</span></span>

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] <span data-ttu-id="785a3-112">安裝 Visual Studio 電腦上安裝。</span><span class="sxs-lookup"><span data-stu-id="785a3-112">installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="785a3-113">Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="785a3-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="785a3-114">建立專案</span><span class="sxs-lookup"><span data-stu-id="785a3-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="785a3-115">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="785a3-115">To create and set up the project</span></span>

1. <span data-ttu-id="785a3-116">建立 WPF 應用程式專案，名為`HostingAxInWpf`。</span><span class="sxs-lookup"><span data-stu-id="785a3-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="785a3-117">將 Windows Form 控制項程式庫專案加入方案，並將專案命名`WmpAxLib`。</span><span class="sxs-lookup"><span data-stu-id="785a3-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="785a3-118">在 WmpAxLib 專案中加入名為 wmp.dll，Windows Media Player 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="785a3-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="785a3-119">開啟**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="785a3-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="785a3-120">以滑鼠右鍵按一下**工具箱**，然後按一下**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="785a3-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="785a3-121">按一下  **COM 元件**索引標籤上，選取**Windows Media Player**控制項，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="785a3-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="785a3-122">Windows Media Player 控制項加入至**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="785a3-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="785a3-123">在 [方案總管] 中，以滑鼠右鍵按一下**UserControl1**檔案，然後再按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="785a3-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="785a3-124">將名稱變更為`WmpAxControl.vb`或`WmpAxControl.cs`，取決於語言。</span><span class="sxs-lookup"><span data-stu-id="785a3-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="785a3-125">如果提示您重新命名所有參考時，請按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="785a3-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="785a3-126">建立 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="785a3-126">Creating the ActiveX Control</span></span>
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] <span data-ttu-id="785a3-127">會自動產生<xref:System.Windows.Forms.AxHost>Microsoft ActiveX 控制項時，控制項會加入至設計介面的包裝函式類別。</span><span class="sxs-lookup"><span data-stu-id="785a3-127">automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="785a3-128">下列程序會建立名為 AxInterop.WMPLib.dll managed 組件。</span><span class="sxs-lookup"><span data-stu-id="785a3-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="785a3-129">若要建立 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="785a3-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="785a3-130">在 Windows Form 設計工具中開啟 WmpAxControl.vb 或 WmpAxControl.cs。</span><span class="sxs-lookup"><span data-stu-id="785a3-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="785a3-131">從**工具箱**，將 Windows Media Player 控制項加入設計介面。</span><span class="sxs-lookup"><span data-stu-id="785a3-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="785a3-132">在 屬性 視窗中，設定 Windows Media Player 控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="785a3-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="785a3-133">建置 WmpAxLib 控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="785a3-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="785a3-134">裝載 WPF 頁面上的 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="785a3-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="785a3-135">若要裝載 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="785a3-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="785a3-136">在 HostingAxInWpf 專案中加入所產生的 ActiveX 互通性組件的參考。</span><span class="sxs-lookup"><span data-stu-id="785a3-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="785a3-137">這個組件名為 AxInterop.WMPLib.dll，並已新增至 WmpAxLib 專案的偵錯資料夾中，當您匯入 Windows Media Player 控制項。</span><span class="sxs-lookup"><span data-stu-id="785a3-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="785a3-138">加入名為 WindowsFormsIntegration.dll 之 WindowsFormsIntegration 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="785a3-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="785a3-139">將參考加入[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名為 System.Windows.Forms.dll 組件。</span><span class="sxs-lookup"><span data-stu-id="785a3-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="785a3-140">WPF Designer 中開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="785a3-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="785a3-141">名稱<xref:System.Windows.Controls.Grid>項目`grid1`。</span><span class="sxs-lookup"><span data-stu-id="785a3-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="785a3-142">在 設計 檢視或 XAML 檢視中，選取 <xref:System.Windows.Window>項目。</span><span class="sxs-lookup"><span data-stu-id="785a3-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="785a3-143">在 屬性 視窗中，按一下**事件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="785a3-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="785a3-144">按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="785a3-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="785a3-145">插入下列程式碼來處理<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="785a3-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="785a3-146">此程式碼建立的執行個體<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項，並將執行個體加入`AxWindowsMediaPlayer`為其子系的控制項。</span><span class="sxs-lookup"><span data-stu-id="785a3-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="785a3-147">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="785a3-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="785a3-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="785a3-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="785a3-149">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="785a3-149">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="785a3-150">逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="785a3-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="785a3-151">逐步解說：裝載 Windows Forms 中的 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="785a3-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
