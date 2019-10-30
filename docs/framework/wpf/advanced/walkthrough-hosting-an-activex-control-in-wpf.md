---
title: 逐步解說：在 WPF 中裝載 ActiveX 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 959bc7942eaae91c0a7a72124f6ab1ab92a3553f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040830"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="c2d89-102">逐步解說：在 WPF 中裝載 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="c2d89-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="c2d89-103">若要改善與瀏覽器的互動，您可以在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中使用 Microsoft ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="c2d89-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="c2d89-104">本逐步解說會示範如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上裝載 Microsoft Windows 媒體播放機做為控制項。</span><span class="sxs-lookup"><span data-stu-id="c2d89-104">This walkthrough demonstrates how you can host the Microsoft Windows Media Player as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="c2d89-105">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="c2d89-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="c2d89-106">建立專案。</span><span class="sxs-lookup"><span data-stu-id="c2d89-106">Creating the project.</span></span>

- <span data-ttu-id="c2d89-107">建立 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="c2d89-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="c2d89-108">將 ActiveX 控制項裝載在 WPF 頁面上。</span><span class="sxs-lookup"><span data-stu-id="c2d89-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="c2d89-109">當您完成本逐步解說時，您將瞭解如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中使用 Microsoft ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="c2d89-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c2d89-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c2d89-110">Prerequisites</span></span>
 <span data-ttu-id="c2d89-111">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="c2d89-111">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="c2d89-112">安裝 Visual Studio 的電腦上安裝了 Microsoft Windows 媒體播放機。</span><span class="sxs-lookup"><span data-stu-id="c2d89-112">Microsoft Windows Media Player installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="c2d89-113">Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="c2d89-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="c2d89-114">建立專案</span><span class="sxs-lookup"><span data-stu-id="c2d89-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="c2d89-115">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="c2d89-115">To create and set up the project</span></span>

1. <span data-ttu-id="c2d89-116">建立名為 `HostingAxInWpf`的 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="c2d89-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="c2d89-117">將 Windows Forms 控制項程式庫專案新增至方案，並將專案命名為 `WmpAxLib`。</span><span class="sxs-lookup"><span data-stu-id="c2d89-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="c2d89-118">在 WmpAxLib 專案中，加入名為 wmp 的 Windows 媒體播放機元件的參考。</span><span class="sxs-lookup"><span data-stu-id="c2d89-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="c2d89-119">開啟 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="c2d89-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="c2d89-120">在 [**工具箱**] 中按一下滑鼠右鍵，然後按一下 **[選擇專案**]。</span><span class="sxs-lookup"><span data-stu-id="c2d89-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="c2d89-121">按一下 [ **COM 元件**] 索引標籤，選取 [ **Windows 媒體播放機**] 控制項，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="c2d89-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="c2d89-122">Windows 媒體播放機控制項就會加入 [**工具箱**] 中。</span><span class="sxs-lookup"><span data-stu-id="c2d89-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="c2d89-123">在方案總管中，以滑鼠右鍵按一下**UserControl1**檔案，然後按一下 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="c2d89-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="c2d89-124">視語言而定，將名稱變更為 `WmpAxControl.vb` 或 `WmpAxControl.cs`。</span><span class="sxs-lookup"><span data-stu-id="c2d89-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="c2d89-125">如果系統提示您重新命名所有參考，請按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="c2d89-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="c2d89-126">建立 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="c2d89-126">Creating the ActiveX Control</span></span>
<span data-ttu-id="c2d89-127">當控制項加入至設計介面時，Visual Studio 會自動為 Microsoft ActiveX 控制項產生 <xref:System.Windows.Forms.AxHost> 的包裝函式類別。</span><span class="sxs-lookup"><span data-stu-id="c2d89-127">Visual Studio automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="c2d89-128">下列程式會建立名為 AxInterop. WMPLib 的 managed 元件。</span><span class="sxs-lookup"><span data-stu-id="c2d89-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="c2d89-129">若要建立 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="c2d89-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="c2d89-130">在 Windows Form 設計工具中開啟 WmpAxControl 或 WmpAxControl.cs。</span><span class="sxs-lookup"><span data-stu-id="c2d89-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="c2d89-131">從 [**工具箱**] 中，將 Windows 媒體播放機控制項加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="c2d89-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="c2d89-132">在屬性視窗中，將 Windows 媒體播放機控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值設定為 [<xref:System.Windows.Forms.DockStyle.Fill>]。</span><span class="sxs-lookup"><span data-stu-id="c2d89-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="c2d89-133">建立 WmpAxLib 控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="c2d89-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="c2d89-134">在 WPF 頁面上裝載 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="c2d89-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="c2d89-135">裝載 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="c2d89-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="c2d89-136">在 HostingAxInWpf 專案中，新增所產生 ActiveX 互通性元件的參考。</span><span class="sxs-lookup"><span data-stu-id="c2d89-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="c2d89-137">這個元件名為 AxInterop. WMPLib，而當您匯入 Windows 媒體播放機控制項時，會加入至 WmpAxLib 專案的 Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c2d89-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="c2d89-138">加入 WindowsFormsIntegration 元件的參考，其名稱為 WindowsFormsIntegration。</span><span class="sxs-lookup"><span data-stu-id="c2d89-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="c2d89-139">將參考加入至名為 System.web 的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="c2d89-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="c2d89-140">在 WPF 設計工具中開啟 Mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="c2d89-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="c2d89-141">將 <xref:System.Windows.Controls.Grid> 元素命名為 `grid1`。</span><span class="sxs-lookup"><span data-stu-id="c2d89-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="c2d89-142">在設計檢視或 XAML 視圖中，選取 [<xref:System.Windows.Window>] 元素。</span><span class="sxs-lookup"><span data-stu-id="c2d89-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="c2d89-143">在 屬性視窗中，按一下 **事件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c2d89-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="c2d89-144">按兩下 [<xref:System.Windows.FrameworkElement.Loaded>] 事件。</span><span class="sxs-lookup"><span data-stu-id="c2d89-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="c2d89-145">插入下列程式碼以處理 <xref:System.Windows.FrameworkElement.Loaded> 事件。</span><span class="sxs-lookup"><span data-stu-id="c2d89-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="c2d89-146">此程式碼會建立 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的實例，並將 `AxWindowsMediaPlayer` 控制項的實例當做其子系加入。</span><span class="sxs-lookup"><span data-stu-id="c2d89-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="c2d89-147">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2d89-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d89-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="c2d89-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c2d89-149">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="c2d89-149">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="c2d89-150">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="c2d89-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="c2d89-151">逐步解說：在 Windows Form 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="c2d89-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
