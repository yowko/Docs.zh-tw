---
title: 逐步解說：在 WPF 中裝載 ActiveX 控制項
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc4f577da04fb8ed15bae3c0497b35803a46f08f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="a8734-102">逐步解說：在 WPF 中裝載 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="a8734-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="a8734-103">若要啟用改善的瀏覽器互動，您可以使用[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]控制在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式。</span><span class="sxs-lookup"><span data-stu-id="a8734-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="a8734-104">本逐步解說示範您可以主控[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]上的控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="a8734-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>  
  
 <span data-ttu-id="a8734-105">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="a8734-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a8734-106">建立專案。</span><span class="sxs-lookup"><span data-stu-id="a8734-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="a8734-107">建立 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="a8734-107">Creating the ActiveX control.</span></span>  
  
-   <span data-ttu-id="a8734-108">ActiveX 控制項裝載到 WPF 頁面上。</span><span class="sxs-lookup"><span data-stu-id="a8734-108">Hosting the ActiveX control on a WPF Page.</span></span>  
  
 <span data-ttu-id="a8734-109">當您完成這個逐步解說時，您將了解如何使用[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]控制中的程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a8734-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8734-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="a8734-110">Prerequisites</span></span>  
 <span data-ttu-id="a8734-111">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="a8734-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]<span data-ttu-id="a8734-112"> 安裝 Visual Studio 電腦上安裝。</span><span class="sxs-lookup"><span data-stu-id="a8734-112"> installed on the computer where Visual Studio is installed.</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="a8734-113">.</span><span class="sxs-lookup"><span data-stu-id="a8734-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a8734-114">建立專案</span><span class="sxs-lookup"><span data-stu-id="a8734-114">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="a8734-115">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="a8734-115">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="a8734-116">建立 WPF 應用程式專案，名為`HostingAxInWpf`。</span><span class="sxs-lookup"><span data-stu-id="a8734-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>  
  
2.  <span data-ttu-id="a8734-117">將 Windows Form 控制項程式庫專案加入方案，並將專案命名`WmpAxLib`。</span><span class="sxs-lookup"><span data-stu-id="a8734-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>  
  
3.  <span data-ttu-id="a8734-118">在 WmpAxLib 專案中，加入名為 wmp.dll 的 Windows Media Player 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="a8734-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>  
  
4.  <span data-ttu-id="a8734-119">開啟**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="a8734-119">Open the **Toolbox**.</span></span>  
  
5.  <span data-ttu-id="a8734-120">以滑鼠右鍵按一下**工具箱**，然後按一下 **選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="a8734-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>  
  
6.  <span data-ttu-id="a8734-121">按一下**COM 元件**索引標籤上，選取**Windows Media Player**控制項，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a8734-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a8734-122">Windows Media Player 控制項加入至**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="a8734-122">The Windows Media Player control is added to the **Toolbox**.</span></span>  
  
7.  <span data-ttu-id="a8734-123">在 [方案總管] 中，以滑鼠右鍵按一下**UserControl1**檔案，然後再按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="a8734-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>  
  
8.  <span data-ttu-id="a8734-124">將名稱變更為`WmpAxControl.vb`或`WmpAxControl.cs`，取決於語言。</span><span class="sxs-lookup"><span data-stu-id="a8734-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>  
  
9. <span data-ttu-id="a8734-125">如果提示您重新命名的所有參考時，請按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="a8734-125">If you are prompted to rename all references, click **Yes**.</span></span>  
  
## <a name="creating-the-activex-control"></a><span data-ttu-id="a8734-126">建立 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="a8734-126">Creating the ActiveX Control</span></span>  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]<span data-ttu-id="a8734-127"> 會自動產生<xref:System.Windows.Forms.AxHost>包裝函式類別[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]控制控制項加入至設計介面時。</span><span class="sxs-lookup"><span data-stu-id="a8734-127"> automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="a8734-128">下列程序會建立名為 AxInterop.WMPLib.dll managed 組件。</span><span class="sxs-lookup"><span data-stu-id="a8734-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>  
  
#### <a name="to-create-the-activex-control"></a><span data-ttu-id="a8734-129">若要建立 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="a8734-129">To create the ActiveX control</span></span>  
  
1.  <span data-ttu-id="a8734-130">在 Windows Form 設計工具中開啟 WmpAxControl.vb 或 WmpAxControl.cs。</span><span class="sxs-lookup"><span data-stu-id="a8734-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="a8734-131">從**工具箱**，將 Windows Media Player 控制項加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a8734-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>  
  
3.  <span data-ttu-id="a8734-132">在 [屬性] 視窗中，將 Windows Media Player 控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="a8734-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
4.  <span data-ttu-id="a8734-133">建置 WmpAxLib 控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="a8734-133">Build the WmpAxLib control library project.</span></span>  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="a8734-134">裝載 WPF 頁面上的 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="a8734-134">Hosting the ActiveX Control on a WPF Page</span></span>  
  
#### <a name="to-host-the-activex-control"></a><span data-ttu-id="a8734-135">裝載 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="a8734-135">To host the ActiveX control</span></span>  
  
1.  <span data-ttu-id="a8734-136">在 HostingAxInWpf 專案中，新增至所產生的參考[!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)]互通性組件。</span><span class="sxs-lookup"><span data-stu-id="a8734-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>  
  
     <span data-ttu-id="a8734-137">這個組件名為 AxInterop.WMPLib.dll，並且已加入至 WmpAxLib 專案的 Debug 資料夾中，當您匯入 Windows Media Player 控制項。</span><span class="sxs-lookup"><span data-stu-id="a8734-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>  
  
2.  <span data-ttu-id="a8734-138">加入名為 WindowsFormsIntegration.dll WindowsFormsIntegration 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="a8734-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="a8734-139">將參考加入[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]System.Windows.Forms.dll 名為組件。</span><span class="sxs-lookup"><span data-stu-id="a8734-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>  
  
4.  <span data-ttu-id="a8734-140">在 WPF 設計工具中開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="a8734-140">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
5.  <span data-ttu-id="a8734-141">名稱<xref:System.Windows.Controls.Grid>元素`grid1`。</span><span class="sxs-lookup"><span data-stu-id="a8734-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  <span data-ttu-id="a8734-142">在 [設計] 檢視或 [XAML] 檢視中，選取<xref:System.Windows.Window>項目。</span><span class="sxs-lookup"><span data-stu-id="a8734-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
7.  <span data-ttu-id="a8734-143">在 屬性 視窗中，按一下**事件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a8734-143">In the Properties window, click the **Events** tab.</span></span>  
  
8.  <span data-ttu-id="a8734-144">按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="a8734-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
9. <span data-ttu-id="a8734-145">插入下列程式碼來處理<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="a8734-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     <span data-ttu-id="a8734-146">此程式碼建立的執行個體<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制，並將執行個體`AxWindowsMediaPlayer`做為其子系的控制項。</span><span class="sxs-lookup"><span data-stu-id="a8734-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="a8734-147">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a8734-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8734-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8734-148">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="a8734-149">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="a8734-149">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="a8734-150">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="a8734-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="a8734-151">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="a8734-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
