---
title: 逐步解說：在 Windows Forms 中裝載立體 WPF 複合控制項
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: e5b98a33f29759a81ba1cbc1fefbd45c0e5bf736
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330164"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="28513-102">逐步解說：在 Windows Forms 中裝載立體 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="28513-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="28513-103">本逐步解說將示範如何建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項，並將它裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項和表單使用<xref:System.Windows.Forms.Integration.ElementHost>控制項。</span><span class="sxs-lookup"><span data-stu-id="28513-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="28513-104">在此逐步解說中，您將實作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>包含兩個子控制項。</span><span class="sxs-lookup"><span data-stu-id="28513-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="28513-105"><xref:System.Windows.Controls.UserControl>顯示三維 (3-D) 圓錐式。</span><span class="sxs-lookup"><span data-stu-id="28513-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="28513-106">呈現 3d 物件是更為容易[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]比使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="28513-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="28513-107">因此，它對有意義主機[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>類別來建立 3d 圖形[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="28513-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

<span data-ttu-id="28513-108">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="28513-108">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="28513-109">建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="28513-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

-   <span data-ttu-id="28513-110">建立 Windows Forms 主應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="28513-110">Creating the Windows Forms host project.</span></span>

-   <span data-ttu-id="28513-111">裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="28513-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28513-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="28513-112">Prerequisites</span></span>

<span data-ttu-id="28513-113">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="28513-113">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="28513-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="28513-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="28513-115">建立使用者控制項</span><span class="sxs-lookup"><span data-stu-id="28513-115">Create the UserControl</span></span>

1. <span data-ttu-id="28513-116">建立**WPF 使用者控制項程式庫**專案，命名為`HostingWpfUserControlInWf`。</span><span class="sxs-lookup"><span data-stu-id="28513-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="28513-117">開啟在 UserControl1.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="28513-117">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

3. <span data-ttu-id="28513-118">產生的程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="28513-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="28513-119">此程式碼定義<xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>包含兩個子控制項。</span><span class="sxs-lookup"><span data-stu-id="28513-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="28513-120">第一個子控制項<xref:System.Windows.Controls.Label?displayProperty=nameWithType>控制項，第二個是<xref:System.Windows.Controls.Viewport3D>顯示 3d 圓錐式控制項。</span><span class="sxs-lookup"><span data-stu-id="28513-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="28513-121">建立主應用程式專案</span><span class="sxs-lookup"><span data-stu-id="28513-121">Create the host project</span></span>

1. <span data-ttu-id="28513-122">新增**WPF 應用程式 (.NET Framework)** 專案，命名為`WpfUserControlHost`至方案。</span><span class="sxs-lookup"><span data-stu-id="28513-122">Add a **WPF App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="28513-123">如需詳細資訊，請參閱[逐步解說：我第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="28513-123">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="28513-124">在 [**方案總管] 中**，加入名為 WindowsFormsIntegration.dll 之 WindowsFormsIntegration 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="28513-124">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="28513-125">將參考加入至下列[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組件：</span><span class="sxs-lookup"><span data-stu-id="28513-125">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    -   <span data-ttu-id="28513-126">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="28513-126">PresentationCore</span></span>

    -   <span data-ttu-id="28513-127">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="28513-127">PresentationFramework</span></span>

    -   <span data-ttu-id="28513-128">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="28513-128">WindowsBase</span></span>

4. <span data-ttu-id="28513-129">加入 `HostingWpfUserControlInWf` 專案的參考。</span><span class="sxs-lookup"><span data-stu-id="28513-129">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="28513-130">在 [方案總管] 中，設定`WpfUserControlHost`專案是啟始專案。</span><span class="sxs-lookup"><span data-stu-id="28513-130">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="28513-131">裝載使用者控制項</span><span class="sxs-lookup"><span data-stu-id="28513-131">Host the UserControl</span></span>

1. <span data-ttu-id="28513-132">在 Windows Form 設計工具中，開啟 Form1。</span><span class="sxs-lookup"><span data-stu-id="28513-132">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="28513-133">在 [屬性] 視窗中，按一下**事件**，然後按兩下<xref:System.Windows.Forms.Form.Load>事件建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="28513-133">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="28513-134">以新產生的程式碼編輯器中開啟`Form1_Load`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="28513-134">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="28513-135">取代為下列程式碼的 Form1.cs 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="28513-135">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="28513-136">`Form1_Load`事件處理常式建立的執行個體`UserControl1`，並將與<xref:System.Windows.Forms.Integration.ElementHost>子控制項的控制項的集合。</span><span class="sxs-lookup"><span data-stu-id="28513-136">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="28513-137"><xref:System.Windows.Forms.Integration.ElementHost>控制項加入至表單的集合中的子控制項。</span><span class="sxs-lookup"><span data-stu-id="28513-137">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="28513-138">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="28513-138">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="28513-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28513-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="28513-140">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="28513-140">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="28513-141">逐步解說：裝載 Windows Forms 中的 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="28513-141">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="28513-142">逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="28513-142">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="28513-143">裝載 WPF 複合控制項在 Windows Form 範例</span><span class="sxs-lookup"><span data-stu-id="28513-143">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)