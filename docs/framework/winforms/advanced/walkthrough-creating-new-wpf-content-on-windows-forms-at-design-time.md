---
title: 逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: ed48db399ba47f0e6be96f7bca33d3892b19e433
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707907"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="703bb-102">逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="703bb-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>

<span data-ttu-id="703bb-103">本主題示範如何建立 Windows Presentation Foundation (WPF) 控制項，以便在 Windows Form 應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="703bb-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

<span data-ttu-id="703bb-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="703bb-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="703bb-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="703bb-105">Create the project.</span></span>

- <span data-ttu-id="703bb-106">建立新的 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="703bb-106">Create a new WPF control.</span></span>

- <span data-ttu-id="703bb-107">將新的 WPF 控制項加入 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="703bb-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="703bb-108">WPF 控制項裝載於 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="703bb-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="703bb-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="703bb-109">Prerequisites</span></span>

<span data-ttu-id="703bb-110">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="703bb-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="703bb-111">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="703bb-111">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="703bb-112">建立專案</span><span class="sxs-lookup"><span data-stu-id="703bb-112">Creating the Project</span></span>

<span data-ttu-id="703bb-113">第一個步驟是建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="703bb-113">The first step is to create the Windows Forms project.</span></span> <span data-ttu-id="703bb-114">開啟 Visual Studio 並建立新**Windows Forms 應用程式 (.NET Framework)** 專案在 Visual Basic 或 Visual C# 中名為`HostingWpf`。</span><span class="sxs-lookup"><span data-stu-id="703bb-114">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="703bb-115">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="703bb-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="703bb-116">建立新的 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="703bb-116">Creating a New WPF Control</span></span>

<span data-ttu-id="703bb-117">建立新的 WPF 控制項並將其加入專案中，就像是將其他任何項目加入專案中一樣容易。</span><span class="sxs-lookup"><span data-stu-id="703bb-117">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="703bb-118">Windows Form 設計工具搭配特定的一種控制項稱為*複合控制項*，或*使用者控制*。</span><span class="sxs-lookup"><span data-stu-id="703bb-118">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="703bb-119">如需 WPF 使用者控制項的詳細資訊，請參閱 <xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="703bb-119">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="703bb-120">WPF 的 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> 類型不同於 Windows Form 所提供的使用者控制項類型 (又稱為 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="703bb-120">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="703bb-121">建立新的 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="703bb-121">To create a new WPF control</span></span>

1. <span data-ttu-id="703bb-122">在 **方案總管**，加入新**WPF 使用者控制項程式庫 (.NET Framework)** 專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="703bb-122">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="703bb-123">使用控制項程式庫的預設名稱 `WpfControlLibrary1`。</span><span class="sxs-lookup"><span data-stu-id="703bb-123">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="703bb-124">預設控制項名稱為 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="703bb-124">The default control name is `UserControl1.xaml`.</span></span>

     <span data-ttu-id="703bb-125">加入新的控制項具有下列效果：</span><span class="sxs-lookup"><span data-stu-id="703bb-125">Adding the new control has the following effects:</span></span>

    - <span data-ttu-id="703bb-126">會加入 UserControl1.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="703bb-126">File UserControl1.xaml is added.</span></span>

    - <span data-ttu-id="703bb-127">會加入 UserControl1.xaml.cs 或 UserControl1.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="703bb-127">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="703bb-128">這個檔案包含事件處理常式和其他實作的程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="703bb-128">This file contains the code-behind for event handlers and other implementation.</span></span>

    - <span data-ttu-id="703bb-129">會加入 WPF 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="703bb-129">References to WPF assemblies are added.</span></span>

    - <span data-ttu-id="703bb-130">UserControl1.xaml 檔案會在 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="703bb-130">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>

2. <span data-ttu-id="703bb-131">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="703bb-131">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="703bb-132">如需詳細資訊，請參閱[如何：選取並移動設計介面上的項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="703bb-132">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="703bb-133">在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以**200**。</span><span class="sxs-lookup"><span data-stu-id="703bb-133">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="703bb-134">從**工具箱**，拖曳<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>控制項拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="703bb-134">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="703bb-135">在 **屬性**視窗中，設定的值<xref:System.Windows.Controls.TextBox.Text%2A>屬性設**裝載內容**。</span><span class="sxs-lookup"><span data-stu-id="703bb-135">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="703bb-136">一般而言，您應該裝載更複雜的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="703bb-136">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="703bb-137"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項在此僅供說明用途使用。</span><span class="sxs-lookup"><span data-stu-id="703bb-137">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="703bb-138">建置專案。</span><span class="sxs-lookup"><span data-stu-id="703bb-138">Build the project.</span></span>

## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="703bb-139">將 WPF 控制項加入 Windows Form</span><span class="sxs-lookup"><span data-stu-id="703bb-139">Adding a WPF Control to a Windows Form</span></span>

<span data-ttu-id="703bb-140">您的新 WPF 控制項已經準備好在表單上使用。</span><span class="sxs-lookup"><span data-stu-id="703bb-140">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="703bb-141">Windows Form 使用<xref:System.Windows.Forms.Integration.ElementHost>裝載 WPF 內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="703bb-141">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="703bb-142">將 WPF 控制項加入 Windows Form</span><span class="sxs-lookup"><span data-stu-id="703bb-142">To add a WPF control to a Windows Form</span></span>

1. <span data-ttu-id="703bb-143">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="703bb-143">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="703bb-144">在 **工具箱**，尋找標示為  索引標籤**WPFUserControlLibrary WPF 使用者控制項**。</span><span class="sxs-lookup"><span data-stu-id="703bb-144">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="703bb-145">將 `UserControl1` 的執行個體拖曳到表單上。</span><span class="sxs-lookup"><span data-stu-id="703bb-145">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="703bb-146"><xref:System.Windows.Forms.Integration.ElementHost> 控制項會在表單上自動建立，以裝載 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="703bb-146">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="703bb-147"><xref:System.Windows.Forms.Integration.ElementHost>控制項的名稱為`elementHost1`然後在**屬性**視窗中，您可以看到其<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>屬性設為**UserControl1**。</span><span class="sxs-lookup"><span data-stu-id="703bb-147">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="703bb-148">WPF 組件的參考會加入專案中。</span><span class="sxs-lookup"><span data-stu-id="703bb-148">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="703bb-149">`elementHost1` 控制項具有智慧標籤面板，這個面板會顯示可用的裝載選項。</span><span class="sxs-lookup"><span data-stu-id="703bb-149">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="703bb-150">在  **ElementHost 工作**智慧標籤面板中，選取**停駐於父容器**。</span><span class="sxs-lookup"><span data-stu-id="703bb-150">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="703bb-151">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="703bb-151">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="703bb-152">後續步驟</span><span class="sxs-lookup"><span data-stu-id="703bb-152">Next Steps</span></span>

<span data-ttu-id="703bb-153">Windows Form 和 WPF 是不同的技術，不過可以藉由設計密切地相互操作。</span><span class="sxs-lookup"><span data-stu-id="703bb-153">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="703bb-154">若要提供更豐富的外觀和行為在您的應用程式，請嘗試下列方法：</span><span class="sxs-lookup"><span data-stu-id="703bb-154">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="703bb-155">將 Windows Form 控制項裝載到 WPF 頁面中。</span><span class="sxs-lookup"><span data-stu-id="703bb-155">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="703bb-156">如需詳細資訊，請參閱[逐步解說：在 WPF 中裝載 Windows Forms 控制項](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="703bb-156">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="703bb-157">將 Windows Form 視覺化樣式套用至 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="703bb-157">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="703bb-158">如需詳細資訊，請參閱[如何：啟用混合式應用程式中的視覺化樣式](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)。</span><span class="sxs-lookup"><span data-stu-id="703bb-158">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="703bb-159">變更 WPF 內容的樣式。</span><span class="sxs-lookup"><span data-stu-id="703bb-159">Change the style of your WPF content.</span></span> <span data-ttu-id="703bb-160">如需詳細資訊，請參閱[逐步解說：設定 WPF 內容的樣式](walkthrough-styling-wpf-content.md)。</span><span class="sxs-lookup"><span data-stu-id="703bb-160">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="703bb-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="703bb-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="703bb-162">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="703bb-162">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="703bb-163">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="703bb-163">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="703bb-164">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="703bb-164">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
