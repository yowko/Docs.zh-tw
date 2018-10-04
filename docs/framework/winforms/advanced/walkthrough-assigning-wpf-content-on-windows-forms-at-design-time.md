---
title: 逐步解說：在設計階段指派 Windows Form 的 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 554153335c08c9c8911a5d4fda3696db1e0abf2a
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48264222"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="a4b4a-102">逐步解說：在設計階段指派 Windows Form 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="a4b4a-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="a4b4a-103">本逐步解說示範如何選取要在表單上顯示的 Windows Presentation Foundation (WPF) 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="a4b4a-104">您可以選取包含在專案中的任何 WPF 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-104">You can select any WPF control types which are included in your project.</span></span>

 <span data-ttu-id="a4b4a-105">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="a4b4a-105">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="a4b4a-106">建立專案。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-106">Create the project.</span></span>

-   <span data-ttu-id="a4b4a-107">建立 WPF 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-107">Create the WPF control types.</span></span>

-   <span data-ttu-id="a4b4a-108">選取 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-108">Select WPF controls.</span></span>

> [!NOTE]
>  <span data-ttu-id="a4b4a-109">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a4b4a-110">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a4b4a-111">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a4b4a-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="a4b4a-112">Prerequisites</span></span>  
 <span data-ttu-id="a4b4a-113">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="a4b4a-113">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="a4b4a-114">Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-114">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a4b4a-115">建立專案</span><span class="sxs-lookup"><span data-stu-id="a4b4a-115">Creating the Project</span></span>  
 <span data-ttu-id="a4b4a-116">第一個步驟是建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4b4a-117">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="a4b4a-118">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="a4b4a-118">To create the project</span></span>  
  
-   <span data-ttu-id="a4b4a-119">建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`SelectingWpfContent`。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="a4b4a-120">建立 WPF 控制項類型</span><span class="sxs-lookup"><span data-stu-id="a4b4a-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="a4b4a-121">當您將 WPF 控制項類型加入專案之後，即可在不同的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中裝載這些類型。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="a4b4a-122">建立 WPF 控制項類型</span><span class="sxs-lookup"><span data-stu-id="a4b4a-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="a4b4a-123">將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="a4b4a-124">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="a4b4a-125">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立新 WPF 內容在設計階段的 Windows Form 上](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="a4b4a-126">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="a4b4a-127">如需詳細資訊，請參閱 <<c0> [ 如何： 選取和移動設計介面上的項目](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474)。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-127">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="a4b4a-128">在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="a4b4a-129">新增<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>若要控制<xref:System.Windows.Controls.UserControl>並將值<xref:System.Windows.Controls.TextBox.Text%2A>屬性設**裝載內容**。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="a4b4a-130">將第二個 WPF <xref:System.Windows.Controls.UserControl> 加入專案。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="a4b4a-131">使用控制項類型的預設名稱 `UserControl2.xaml`。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="a4b4a-132">在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="a4b4a-133">新增<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>若要控制<xref:System.Windows.Controls.UserControl>並將值<xref:System.Windows.Controls.TextBox.Text%2A>屬性設**裝載的內容 2**。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="a4b4a-134">**請注意**一般情況下，您應該裝載更複雜的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="a4b4a-135"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項在此僅供說明用途使用。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="a4b4a-136">建置專案。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="a4b4a-137">選取 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="a4b4a-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="a4b4a-138">您可以對已裝載內容的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，指派不同的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="a4b4a-139">選取 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="a4b4a-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="a4b4a-140">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="a4b4a-141">在 **工具箱**，按兩下`UserControl1`若要建立的執行個體`UserControl1`表單上。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="a4b4a-142">`UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="a4b4a-143">中的智慧標籤面板`elementHost1`，開啟**選擇裝載內容**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="a4b4a-144">選取  **UserControl2**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="a4b4a-145">`elementHost1` 控制項現在會裝載 `UserControl2` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="a4b4a-146">在 [**屬性**] 視窗中，確認<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>屬性設定為**UserControl2**。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="a4b4a-147">從**工具箱**，請在**WPF 互通性**群組中，拖曳<xref:System.Windows.Forms.Integration.ElementHost>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="a4b4a-148">新控制項的預設名稱為 `elementHost2`。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="a4b4a-149">中的智慧標籤面板`elementHost2`，開啟**選擇裝載內容**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="a4b4a-150">選取  **UserControl1**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="a4b4a-151">`elementHost2` 控制項現在會裝載 `UserControl1` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4b4a-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b4a-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4b4a-152">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="a4b4a-153">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="a4b4a-153">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="a4b4a-154">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="a4b4a-154">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="a4b4a-155">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="a4b4a-155">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
