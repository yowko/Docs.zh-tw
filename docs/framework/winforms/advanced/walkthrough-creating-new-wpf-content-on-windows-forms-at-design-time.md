---
title: 逐步解說：在設計階段建立 Windows Form 的新 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 1ea0160530fea0f35c6d4746dc4bbca9439bc462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529005"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="81fb2-102">逐步解說：在設計階段建立 Windows Form 的新 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="81fb2-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="81fb2-103">本主題示範如何建立 Windows Presentation Foundation (WPF) 控制項，以便在 Windows Form 應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="81fb2-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>  
  
 <span data-ttu-id="81fb2-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="81fb2-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="81fb2-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="81fb2-105">Create the project.</span></span>  
  
-   <span data-ttu-id="81fb2-106">建立新的 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="81fb2-106">Create a new WPF control.</span></span>  
  
-   <span data-ttu-id="81fb2-107">將新的 WPF 控制項加入 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="81fb2-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="81fb2-108">WPF 控制項裝載於 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="81fb2-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81fb2-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="81fb2-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="81fb2-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="81fb2-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="81fb2-111">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="81fb2-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="81fb2-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="81fb2-112">Prerequisites</span></span>  
 <span data-ttu-id="81fb2-113">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="81fb2-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="81fb2-114">.</span><span class="sxs-lookup"><span data-stu-id="81fb2-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="81fb2-115">建立專案</span><span class="sxs-lookup"><span data-stu-id="81fb2-115">Creating the Project</span></span>  
 <span data-ttu-id="81fb2-116">第一個步驟是建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="81fb2-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81fb2-117">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="81fb2-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="81fb2-118">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="81fb2-118">To create the project</span></span>  
  
-   <span data-ttu-id="81fb2-119">建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`HostingWpf`。</span><span class="sxs-lookup"><span data-stu-id="81fb2-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `HostingWpf`.</span></span>  
  
## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="81fb2-120">建立新的 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="81fb2-120">Creating a New WPF Control</span></span>  
 <span data-ttu-id="81fb2-121">建立新的 WPF 控制項並將其加入專案中，就像是將其他任何項目加入專案中一樣容易。</span><span class="sxs-lookup"><span data-stu-id="81fb2-121">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="81fb2-122">Windows Form 設計工具搭配特定種類的控制項，名為*複合控制項*，或*使用者控制項*。</span><span class="sxs-lookup"><span data-stu-id="81fb2-122">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="81fb2-123">如需 WPF 使用者控制項的詳細資訊，請參閱 <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="81fb2-123">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81fb2-124">WPF 的 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> 類型不同於 Windows Form 所提供的使用者控制項類型 (又稱為 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="81fb2-124">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>  
  
#### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="81fb2-125">建立新的 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="81fb2-125">To create a new WPF control</span></span>  
  
1.  <span data-ttu-id="81fb2-126">在**方案總管 中**，加入新**WPF 使用者控制項程式庫**專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="81fb2-126">In **Solution Explorer**, add a new **WPF User Control Library** project to the solution.</span></span> <span data-ttu-id="81fb2-127">使用控制項程式庫的預設名稱 `WpfControlLibrary1`。</span><span class="sxs-lookup"><span data-stu-id="81fb2-127">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="81fb2-128">預設控制項名稱為 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="81fb2-128">The default control name is `UserControl1.xaml`.</span></span>  
  
     <span data-ttu-id="81fb2-129">加入新的控制項具有下列效果。</span><span class="sxs-lookup"><span data-stu-id="81fb2-129">Adding the new control has the following effects.</span></span>  
  
    -   <span data-ttu-id="81fb2-130">會加入 UserControl1.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="81fb2-130">File UserControl1.xaml is added.</span></span>  
  
    -   <span data-ttu-id="81fb2-131">會加入 UserControl1.xaml.cs 或 UserControl1.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="81fb2-131">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="81fb2-132">這個檔案包含事件處理常式和其他實作的程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="81fb2-132">This file contains the code-behind for event handlers and other implementation.</span></span>  
  
    -   <span data-ttu-id="81fb2-133">會加入 WPF 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="81fb2-133">References to WPF assemblies are added.</span></span>  
  
    -   <span data-ttu-id="81fb2-134">UserControl1.xaml 檔案會在 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="81fb2-134">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="81fb2-135">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="81fb2-135">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="81fb2-136">如需詳細資訊，請參閱[如何： 選取並在設計介面上的 移動項目](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474)。</span><span class="sxs-lookup"><span data-stu-id="81fb2-136">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="81fb2-137">在**屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性`200`。</span><span class="sxs-lookup"><span data-stu-id="81fb2-137">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="81fb2-138">從**工具箱**，拖曳<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>控制項拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="81fb2-138">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>  
  
5.  <span data-ttu-id="81fb2-139">在**屬性**視窗中，設定的值<xref:System.Windows.Controls.TextBox.Text%2A>屬性**裝載內容**。</span><span class="sxs-lookup"><span data-stu-id="81fb2-139">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="81fb2-140">一般而言，您應該裝載更複雜的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="81fb2-140">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="81fb2-141"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項在此僅供說明用途使用。</span><span class="sxs-lookup"><span data-stu-id="81fb2-141">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
6.  <span data-ttu-id="81fb2-142">建置專案。</span><span class="sxs-lookup"><span data-stu-id="81fb2-142">Build the project.</span></span>  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="81fb2-143">將 WPF 控制項加入 Windows Form</span><span class="sxs-lookup"><span data-stu-id="81fb2-143">Adding a WPF Control to a Windows Form</span></span>  
 <span data-ttu-id="81fb2-144">您的新 WPF 控制項已經準備好在表單上使用。</span><span class="sxs-lookup"><span data-stu-id="81fb2-144">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="81fb2-145">Windows Form 會使用 <xref:System.Windows.Forms.Integration.ElementHost> 控制項裝載 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="81fb2-145">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content</span></span>  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="81fb2-146">將 WPF 控制項加入 Windows Form</span><span class="sxs-lookup"><span data-stu-id="81fb2-146">To add a WPF control to a Windows Form</span></span>  
  
1.  <span data-ttu-id="81fb2-147">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="81fb2-147">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="81fb2-148">在**工具箱**，尋找 索引標籤**WPFUserControlLibrary WPF 使用者控制項**。</span><span class="sxs-lookup"><span data-stu-id="81fb2-148">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>  
  
3.  <span data-ttu-id="81fb2-149">將 `UserControl1` 的執行個體拖曳到表單上。</span><span class="sxs-lookup"><span data-stu-id="81fb2-149">Drag an instance of `UserControl1` onto the form.</span></span>  
  
    -   <span data-ttu-id="81fb2-150"><xref:System.Windows.Forms.Integration.ElementHost> 控制項會在表單上自動建立，以裝載 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="81fb2-150">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>  
  
    -   <span data-ttu-id="81fb2-151"><xref:System.Windows.Forms.Integration.ElementHost>控制項名為`elementHost1`和**屬性**視窗中，您可以看到其<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>屬性設定為**UserControl1**。</span><span class="sxs-lookup"><span data-stu-id="81fb2-151">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>  
  
    -   <span data-ttu-id="81fb2-152">WPF 組件的參考會加入專案中。</span><span class="sxs-lookup"><span data-stu-id="81fb2-152">References to WPF assemblies are added to the project.</span></span>  
  
    -   <span data-ttu-id="81fb2-153">`elementHost1` 控制項具有智慧標籤面板，這個面板會顯示可用的裝載選項。</span><span class="sxs-lookup"><span data-stu-id="81fb2-153">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>  
  
4.  <span data-ttu-id="81fb2-154">在**ElementHost 工作**智慧標籤面板中，選取**停駐於父容器**。</span><span class="sxs-lookup"><span data-stu-id="81fb2-154">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>  
  
5.  <span data-ttu-id="81fb2-155">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="81fb2-155">Press F5 to build and run the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="81fb2-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="81fb2-156">Next Steps</span></span>  
 <span data-ttu-id="81fb2-157">Windows Form 和 WPF 是不同的技術，不過可以藉由設計密切地相互操作。</span><span class="sxs-lookup"><span data-stu-id="81fb2-157">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="81fb2-158">若要在應用程式中提供更豐富的外觀和行為，請嘗試下列方法。</span><span class="sxs-lookup"><span data-stu-id="81fb2-158">To provide richer appearance and behavior in your applications, try the following.</span></span>  
  
-   <span data-ttu-id="81fb2-159">將 Windows Form 控制項裝載到 WPF 頁面中。</span><span class="sxs-lookup"><span data-stu-id="81fb2-159">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="81fb2-160">如需詳細資訊，請參閱[逐步解說： 在 WPF 中將 Windows Form 控制項裝載](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="81fb2-160">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
-   <span data-ttu-id="81fb2-161">將 Windows Form 視覺化樣式套用至 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="81fb2-161">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="81fb2-162">如需詳細資訊，請參閱[如何：在混合應用程式中啟用視覺化樣式](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)。</span><span class="sxs-lookup"><span data-stu-id="81fb2-162">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>  
  
-   <span data-ttu-id="81fb2-163">變更 WPF 內容的樣式。</span><span class="sxs-lookup"><span data-stu-id="81fb2-163">Change the style of your WPF content.</span></span> <span data-ttu-id="81fb2-164">如需詳細資訊，請參閱[逐步解說： 設定樣式的 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)。</span><span class="sxs-lookup"><span data-stu-id="81fb2-164">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fb2-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81fb2-165">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="81fb2-166">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="81fb2-166">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="81fb2-167">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="81fb2-167">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="81fb2-168">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="81fb2-168">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
