---
title: 逐步解說：在設計階段指派 Windows Forms 的 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 09427bfc836f40ca9c7aa76f4904bfe7083bf8dc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211228"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="d69c6-102">逐步解說：在設計階段指派 Windows Forms 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="d69c6-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="d69c6-103">本逐步解說示範如何選取要在表單上顯示的 Windows Presentation Foundation (WPF) 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="d69c6-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="d69c6-104">您可以選取包含在專案中的任何 WPF 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="d69c6-104">You can select any WPF control types which are included in your project.</span></span>

<span data-ttu-id="d69c6-105">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d69c6-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="d69c6-106">建立專案。</span><span class="sxs-lookup"><span data-stu-id="d69c6-106">Create the project.</span></span>

- <span data-ttu-id="d69c6-107">建立 WPF 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="d69c6-107">Create the WPF control types.</span></span>

- <span data-ttu-id="d69c6-108">選取 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="d69c6-108">Select WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d69c6-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="d69c6-109">Prerequisites</span></span>

<span data-ttu-id="d69c6-110">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d69c6-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="d69c6-111">建立專案</span><span class="sxs-lookup"><span data-stu-id="d69c6-111">Create the project</span></span>

<span data-ttu-id="d69c6-112">開啟 Visual Studio 並建立新的 Windows Forms 應用程式專案在 Visual Basic 或 VisualC#名為`SelectingWpfContent`。</span><span class="sxs-lookup"><span data-stu-id="d69c6-112">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="d69c6-113">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="d69c6-113">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="d69c6-114">建立 WPF 控制項類型</span><span class="sxs-lookup"><span data-stu-id="d69c6-114">Create the WPF control types</span></span>

<span data-ttu-id="d69c6-115">當您將 WPF 控制項類型加入專案之後，即可在不同的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中裝載這些類型。</span><span class="sxs-lookup"><span data-stu-id="d69c6-115">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

## <a name="create-wpf-control-types"></a><span data-ttu-id="d69c6-116">建立 WPF 控制項類型</span><span class="sxs-lookup"><span data-stu-id="d69c6-116">Create WPF control types</span></span>

1. <span data-ttu-id="d69c6-117">將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="d69c6-117">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="d69c6-118">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="d69c6-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="d69c6-119">如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="d69c6-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="d69c6-120">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="d69c6-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="d69c6-121">如需詳細資訊，請參閱[如何：選取並移動設計介面上的項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d69c6-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="d69c6-122">在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。</span><span class="sxs-lookup"><span data-stu-id="d69c6-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="d69c6-123">新增<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>若要控制<xref:System.Windows.Controls.UserControl>並將值<xref:System.Windows.Controls.TextBox.Text%2A>屬性設**裝載內容**。</span><span class="sxs-lookup"><span data-stu-id="d69c6-123">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="d69c6-124">將第二個 WPF <xref:System.Windows.Controls.UserControl> 加入專案。</span><span class="sxs-lookup"><span data-stu-id="d69c6-124">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="d69c6-125">使用控制項類型的預設名稱 `UserControl2.xaml`。</span><span class="sxs-lookup"><span data-stu-id="d69c6-125">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="d69c6-126">在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。</span><span class="sxs-lookup"><span data-stu-id="d69c6-126">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

7. <span data-ttu-id="d69c6-127">新增<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>若要控制<xref:System.Windows.Controls.UserControl>並將值<xref:System.Windows.Controls.TextBox.Text%2A>屬性設**裝載的內容 2**。</span><span class="sxs-lookup"><span data-stu-id="d69c6-127">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

 <span data-ttu-id="d69c6-128">**請注意**一般情況下，您應該裝載更複雜的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="d69c6-128">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="d69c6-129"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項在此僅供說明用途使用。</span><span class="sxs-lookup"><span data-stu-id="d69c6-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

1. <span data-ttu-id="d69c6-130">建置專案。</span><span class="sxs-lookup"><span data-stu-id="d69c6-130">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="d69c6-131">選取 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="d69c6-131">Select WPF controls</span></span>

<span data-ttu-id="d69c6-132">您可以對已裝載內容的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，指派不同的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="d69c6-132">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="d69c6-133">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="d69c6-133">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="d69c6-134">在 **工具箱**，按兩下`UserControl1`若要建立的執行個體`UserControl1`表單上。</span><span class="sxs-lookup"><span data-stu-id="d69c6-134">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="d69c6-135">`UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="d69c6-135">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="d69c6-136">中的智慧標籤面板`elementHost1`，開啟**選擇裝載內容**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d69c6-136">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="d69c6-137">選取  **UserControl2**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="d69c6-137">Select **UserControl2** from the drop-down list box.</span></span>

     <span data-ttu-id="d69c6-138">`elementHost1` 控制項現在會裝載 `UserControl2` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d69c6-138">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="d69c6-139">在 [**屬性**] 視窗中，確認<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>屬性設定為**UserControl2**。</span><span class="sxs-lookup"><span data-stu-id="d69c6-139">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="d69c6-140">從**工具箱**，請在**WPF 互通性**群組中，拖曳<xref:System.Windows.Forms.Integration.ElementHost>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="d69c6-140">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

     <span data-ttu-id="d69c6-141">新控制項的預設名稱為 `elementHost2`。</span><span class="sxs-lookup"><span data-stu-id="d69c6-141">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="d69c6-142">中的智慧標籤面板`elementHost2`，開啟**選擇裝載內容**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d69c6-142">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="d69c6-143">選取  **UserControl1**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d69c6-143">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="d69c6-144">`elementHost2` 控制項現在會裝載 `UserControl1` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d69c6-144">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="d69c6-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d69c6-145">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="d69c6-146">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="d69c6-146">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="d69c6-147">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="d69c6-147">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="d69c6-148">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="d69c6-148">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
