---
title: "逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5af705509d30f7dfd50ade0c07aca242deff4dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="2e9db-102">逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="2e9db-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>
<span data-ttu-id="2e9db-103">本逐步解說示範如何建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項，以及裝載在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項和表單使用<xref:System.Windows.Forms.Integration.ElementHost>控制項。</span><span class="sxs-lookup"><span data-stu-id="2e9db-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
 <span data-ttu-id="2e9db-104">在本逐步解說，您將實作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> ，其中包含兩個的子控制項。</span><span class="sxs-lookup"><span data-stu-id="2e9db-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="2e9db-105"><xref:System.Windows.Controls.UserControl>三維 (3d) 圓錐圖會顯示。</span><span class="sxs-lookup"><span data-stu-id="2e9db-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="2e9db-106">呈現 3d 物件會更為容易，因為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]比使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2e9db-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="2e9db-107">因此，它可以理解主機[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>類別以建立在 3d 圖形[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2e9db-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="2e9db-108">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="2e9db-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="2e9db-109">建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="2e9db-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
-   <span data-ttu-id="2e9db-110">建立 Windows 表單主應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="2e9db-110">Creating the Windows Forms host project.</span></span>  
  
-   <span data-ttu-id="2e9db-111">裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="2e9db-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>  
  
 <span data-ttu-id="2e9db-112">在此逐步解說中所述的工作的完整程式碼清單，請參閱[裝載 Windows Form 範例中的 3d WPF 複合控制項](http://go.microsoft.com/fwlink/?LinkID=160001)。</span><span class="sxs-lookup"><span data-stu-id="2e9db-112">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a 3-D WPF Composite Control in Windows Forms Sample](http://go.microsoft.com/fwlink/?LinkID=160001).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2e9db-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="2e9db-113">Prerequisites</span></span>  
 <span data-ttu-id="2e9db-114">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="2e9db-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="2e9db-115">.</span><span class="sxs-lookup"><span data-stu-id="2e9db-115">.</span></span>  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a><span data-ttu-id="2e9db-116">建立使用者控制項</span><span class="sxs-lookup"><span data-stu-id="2e9db-116">Creating the UserControl</span></span>  
  
#### <a name="to-create-the-usercontrol"></a><span data-ttu-id="2e9db-117">若要建立使用者控制項</span><span class="sxs-lookup"><span data-stu-id="2e9db-117">To create the UserControl</span></span>  
  
1.  <span data-ttu-id="2e9db-118">建立 WPF 使用者控制項程式庫專案，名為`HostingWpfUserControlInWf`。</span><span class="sxs-lookup"><span data-stu-id="2e9db-118">Create a WPF User Control Library project named `HostingWpfUserControlInWf`.</span></span>  
  
2.  <span data-ttu-id="2e9db-119">開啟 usercontrol1.xaml 檔案中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2e9db-119">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
3.  <span data-ttu-id="2e9db-120">產生的程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="2e9db-120">Replace the generated code with the following code.</span></span>  
  
     <span data-ttu-id="2e9db-121">此程式碼定義<xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>，其中包含兩個的子控制項。</span><span class="sxs-lookup"><span data-stu-id="2e9db-121">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="2e9db-122">第一個子系控制項是<xref:System.Windows.Controls.Label?displayProperty=nameWithType>控制; 第二個是<xref:System.Windows.Controls.Viewport3D>顯示 3d 圓錐控制項。</span><span class="sxs-lookup"><span data-stu-id="2e9db-122">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="2e9db-123">建立 Windows Forms 主專案</span><span class="sxs-lookup"><span data-stu-id="2e9db-123">Creating the Windows Forms Host Project</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="2e9db-124">建立主專案</span><span class="sxs-lookup"><span data-stu-id="2e9db-124">To create the host project</span></span>  
  
1.  <span data-ttu-id="2e9db-125">新增 Windows 應用程式專案，名為`WpfUserControlHost`至方案。</span><span class="sxs-lookup"><span data-stu-id="2e9db-125">Add a Windows application project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="2e9db-126">如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。</span><span class="sxs-lookup"><span data-stu-id="2e9db-126">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="2e9db-127">在方案總管 中，加入名為 WindowsFormsIntegration.dll WindowsFormsIntegration 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="2e9db-127">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="2e9db-128">將參考加入至下列[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組件：</span><span class="sxs-lookup"><span data-stu-id="2e9db-128">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>  
  
    -   <span data-ttu-id="2e9db-129">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="2e9db-129">PresentationCore</span></span>  
  
    -   <span data-ttu-id="2e9db-130">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="2e9db-130">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="2e9db-131">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="2e9db-131">WindowsBase</span></span>  
  
4.  <span data-ttu-id="2e9db-132">加入 `HostingWpfUserControlInWf` 專案的參考。</span><span class="sxs-lookup"><span data-stu-id="2e9db-132">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>  
  
5.  <span data-ttu-id="2e9db-133">在 [方案總管] 中，設定`WpfUserControlHost`專案是啟始專案。</span><span class="sxs-lookup"><span data-stu-id="2e9db-133">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a><span data-ttu-id="2e9db-134">裝載 Windows Presentation Foundation 使用者控制項</span><span class="sxs-lookup"><span data-stu-id="2e9db-134">Hosting the Windows Presentation Foundation UserControl</span></span>  
  
#### <a name="to-host-the-usercontrol"></a><span data-ttu-id="2e9db-135">若要裝載使用者控制項</span><span class="sxs-lookup"><span data-stu-id="2e9db-135">To host the UserControl</span></span>  
  
1.  <span data-ttu-id="2e9db-136">在 Windows Form 設計工具中，開啟 [Form1]。</span><span class="sxs-lookup"><span data-stu-id="2e9db-136">In the Windows Forms Designer, open Form1.</span></span>  
  
2.  <span data-ttu-id="2e9db-137">在 [屬性] 視窗中，按一下**事件**，然後按兩下<xref:System.Windows.Forms.Form.Load>事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2e9db-137">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>  
  
     <span data-ttu-id="2e9db-138">以新產生的程式碼編輯器中開啟`Form1_Load`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2e9db-138">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>  
  
3.  <span data-ttu-id="2e9db-139">在 Form1.cs 中的程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="2e9db-139">Replace the code in Form1.cs with the following code.</span></span>  
  
     <span data-ttu-id="2e9db-140">`Form1_Load`事件處理常式中建立的執行個體`UserControl1`並加入為原<xref:System.Windows.Forms.Integration.ElementHost>子控制項的控制項的集合。</span><span class="sxs-lookup"><span data-stu-id="2e9db-140">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="2e9db-141"><xref:System.Windows.Forms.Integration.ElementHost>控制項會加入至表單的子控制項的集合。</span><span class="sxs-lookup"><span data-stu-id="2e9db-141">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="2e9db-142">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2e9db-142">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9db-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e9db-143">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="2e9db-144">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="2e9db-144">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="2e9db-145">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="2e9db-145">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="2e9db-146">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="2e9db-146">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="2e9db-147">裝載 Windows Form 範例中的 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="2e9db-147">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160001)
