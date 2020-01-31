---
title: 選取 Windows Forms 的 WPF 控制項
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19f1dfec282b025f5a1fa367ec5fa9a52472c691
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746806"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="a8925-102">逐步解說：在設計階段指派 Windows Forms 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="a8925-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="a8925-103">本文說明如何選取您要在表單上顯示的 Windows Presentation Foundation （WPF）控制項類型。</span><span class="sxs-lookup"><span data-stu-id="a8925-103">This article show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="a8925-104">您可以選取包含在專案中的任何 WPF 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="a8925-104">You can select any WPF control types that are included in your project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8925-105">必要條件：</span><span class="sxs-lookup"><span data-stu-id="a8925-105">Prerequisites</span></span>

<span data-ttu-id="a8925-106">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a8925-106">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a8925-107">建立專案</span><span class="sxs-lookup"><span data-stu-id="a8925-107">Create the project</span></span>

<span data-ttu-id="a8925-108">開啟 Visual Studio，並在 Visual Basic 或視覺效果C#中建立名為 `SelectingWpfContent`的新 Windows Forms 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="a8925-108">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="a8925-109">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="a8925-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="a8925-110">建立 WPF 控制項類型</span><span class="sxs-lookup"><span data-stu-id="a8925-110">Create the WPF control types</span></span>

<span data-ttu-id="a8925-111">當您將 WPF 控制項類型加入專案之後，即可在不同的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中裝載這些類型。</span><span class="sxs-lookup"><span data-stu-id="a8925-111">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

1. <span data-ttu-id="a8925-112">將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="a8925-112">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="a8925-113">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="a8925-113">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="a8925-114">如需詳細資訊，請參閱[逐步解說：在設計階段于 Windows Forms 上建立新的 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="a8925-114">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="a8925-115">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="a8925-115">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="a8925-116">在 [**屬性**] 視窗中，將 [<xref:System.Windows.FrameworkElement.Width%2A>] 和 [<xref:System.Windows.FrameworkElement.Height%2A> 屬性] 的值設定為**200**。</span><span class="sxs-lookup"><span data-stu-id="a8925-116">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="a8925-117">將 <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項加入至 <xref:System.Windows.Controls.UserControl>，並將 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的值設定為 [裝載的**內容**]。</span><span class="sxs-lookup"><span data-stu-id="a8925-117">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="a8925-118">將第二個 WPF <xref:System.Windows.Controls.UserControl> 加入專案。</span><span class="sxs-lookup"><span data-stu-id="a8925-118">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="a8925-119">使用控制項類型的預設名稱 `UserControl2.xaml`。</span><span class="sxs-lookup"><span data-stu-id="a8925-119">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="a8925-120">在 [**屬性**] 視窗中，將 [<xref:System.Windows.FrameworkElement.Width%2A>] 和 [<xref:System.Windows.FrameworkElement.Height%2A> 屬性] 的值設定為**200**。</span><span class="sxs-lookup"><span data-stu-id="a8925-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

7. <span data-ttu-id="a8925-121">將 <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項新增至 <xref:System.Windows.Controls.UserControl>，並將 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的值設定為 [裝載的**內容 2**]。</span><span class="sxs-lookup"><span data-stu-id="a8925-121">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a8925-122">一般而言，您應該裝載更複雜的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="a8925-122">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="a8925-123"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控制項在此僅供說明用途使用。</span><span class="sxs-lookup"><span data-stu-id="a8925-123">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

8. <span data-ttu-id="a8925-124">建置專案。</span><span class="sxs-lookup"><span data-stu-id="a8925-124">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="a8925-125">選取 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="a8925-125">Select WPF controls</span></span>

<span data-ttu-id="a8925-126">您可以對已裝載內容的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，指派不同的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="a8925-126">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="a8925-127">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="a8925-127">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="a8925-128">在 [**工具箱**] 中，按兩下 [`UserControl1`]，在表單上建立 `UserControl1` 的實例。</span><span class="sxs-lookup"><span data-stu-id="a8925-128">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="a8925-129">`UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="a8925-129">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="a8925-130">在 `elementHost1`的智慧標籤面板中，開啟 [**選取主控內容**] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a8925-130">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="a8925-131">從下拉式清單方塊中選取  **usercontrol2** 。</span><span class="sxs-lookup"><span data-stu-id="a8925-131">Select **UserControl2** from the drop-down list box.</span></span>

   <span data-ttu-id="a8925-132">`elementHost1` 控制項現在會裝載 `UserControl2` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a8925-132">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="a8925-133">在 **屬性** 視窗中，確認 <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> 屬性已設定為  **usercontrol2**。</span><span class="sxs-lookup"><span data-stu-id="a8925-133">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="a8925-134">從 [**工具箱**] 的 [ **WPF 互通性**] 群組中，將 [<xref:System.Windows.Forms.Integration.ElementHost>] 控制項拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="a8925-134">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

   <span data-ttu-id="a8925-135">新控制項的預設名稱為 `elementHost2`。</span><span class="sxs-lookup"><span data-stu-id="a8925-135">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="a8925-136">在 `elementHost2`的智慧標籤面板中，開啟 [**選取主控內容**] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a8925-136">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="a8925-137">從下拉式清單中選取 [ **UserControl1** ]。</span><span class="sxs-lookup"><span data-stu-id="a8925-137">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="a8925-138">`elementHost2` 控制項現在會裝載 `UserControl1` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a8925-138">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8925-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="a8925-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a8925-140">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="a8925-140">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="a8925-141">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="a8925-141">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="a8925-142">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="a8925-142">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
