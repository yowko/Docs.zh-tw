---
title: 逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: f33adf6bac5efab87fecd9e95437ac8cff6d1f16
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976549"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="4c107-102">逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="4c107-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="4c107-103">本逐步解說將示範如何建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項，並使用 <xref:System.Windows.Forms.Integration.ElementHost> 控制項將它裝載在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項和表單中。</span><span class="sxs-lookup"><span data-stu-id="4c107-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="4c107-104">在此逐步解說中，您將會執行包含兩個子控制項的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="4c107-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="4c107-105"><xref:System.Windows.Controls.UserControl> 會顯示三維（立體）圓錐圖。</span><span class="sxs-lookup"><span data-stu-id="4c107-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="4c107-106">使用與 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]相比，轉譯3D 物件比 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 更容易。</span><span class="sxs-lookup"><span data-stu-id="4c107-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="4c107-107">因此，裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 類別以在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]中建立立體圖形是合理的。</span><span class="sxs-lookup"><span data-stu-id="4c107-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

<span data-ttu-id="4c107-108">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="4c107-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="4c107-109">建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="4c107-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

- <span data-ttu-id="4c107-110">建立 Windows Forms 主專案。</span><span class="sxs-lookup"><span data-stu-id="4c107-110">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="4c107-111">裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="4c107-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4c107-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4c107-112">Prerequisites</span></span>

<span data-ttu-id="4c107-113">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="4c107-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="4c107-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4c107-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="4c107-115">建立 UserControl</span><span class="sxs-lookup"><span data-stu-id="4c107-115">Create the UserControl</span></span>

1. <span data-ttu-id="4c107-116">建立名為 `HostingWpfUserControlInWf`的**WPF 使用者控制項程式庫**專案。</span><span class="sxs-lookup"><span data-stu-id="4c107-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="4c107-117">在 WPF 設計工具中開啟 UserControl1。</span><span class="sxs-lookup"><span data-stu-id="4c107-117">Open UserControl1.xaml in the WPF Designer.</span></span>

3. <span data-ttu-id="4c107-118">將產生的程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4c107-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="4c107-119">此程式碼會定義包含兩個子控制項的 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4c107-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="4c107-120">第一個子控制項是 <xref:System.Windows.Controls.Label?displayProperty=nameWithType> 控制項;第二個是顯示立體錐形的 <xref:System.Windows.Controls.Viewport3D> 控制項。</span><span class="sxs-lookup"><span data-stu-id="4c107-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="4c107-121">建立主專案</span><span class="sxs-lookup"><span data-stu-id="4c107-121">Create the host project</span></span>

1. <span data-ttu-id="4c107-122">將名為 `WpfUserControlHost` 的**Windows Forms 應用程式（.NET Framework）** 專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="4c107-122">Add a **Windows Forms App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span>

2. <span data-ttu-id="4c107-123">在**方案總管**中，加入名為 WindowsFormsIntegration 的 WindowsFormsIntegration 元件參考。</span><span class="sxs-lookup"><span data-stu-id="4c107-123">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="4c107-124">新增下列 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元件的參考：</span><span class="sxs-lookup"><span data-stu-id="4c107-124">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    - <span data-ttu-id="4c107-125">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="4c107-125">PresentationCore</span></span>

    - <span data-ttu-id="4c107-126">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="4c107-126">PresentationFramework</span></span>

    - <span data-ttu-id="4c107-127">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="4c107-127">WindowsBase</span></span>

4. <span data-ttu-id="4c107-128">加入 `HostingWpfUserControlInWf` 專案的參考。</span><span class="sxs-lookup"><span data-stu-id="4c107-128">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="4c107-129">在方案總管中，將 `WpfUserControlHost` 專案設定為啟始專案。</span><span class="sxs-lookup"><span data-stu-id="4c107-129">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="4c107-130">裝載 UserControl</span><span class="sxs-lookup"><span data-stu-id="4c107-130">Host the UserControl</span></span>

1. <span data-ttu-id="4c107-131">在 Windows Form 設計工具中，開啟 Form1。</span><span class="sxs-lookup"><span data-stu-id="4c107-131">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="4c107-132">在 屬性視窗中，按一下 **事件**，然後按兩下 <xref:System.Windows.Forms.Form.Load> 事件來建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4c107-132">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="4c107-133">[程式碼編輯器] 隨即開啟至新產生的 `Form1_Load` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4c107-133">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="4c107-134">將 Form1.cs 中的程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c107-134">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="4c107-135">`Form1_Load` 事件處理常式會建立 `UserControl1` 的實例，並將背後加入至 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的子控制項集合。</span><span class="sxs-lookup"><span data-stu-id="4c107-135">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="4c107-136"><xref:System.Windows.Forms.Integration.ElementHost> 控制項會加入至表單的子控制項集合。</span><span class="sxs-lookup"><span data-stu-id="4c107-136">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="4c107-137">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c107-137">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c107-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c107-138">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="4c107-139">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="4c107-139">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="4c107-140">逐步解說：在 Windows Form 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="4c107-140">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="4c107-141">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="4c107-141">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="4c107-142">在 Windows Forms 範例中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="4c107-142">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)
