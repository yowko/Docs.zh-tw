---
title: 逐步解說：在設計階段排列 Windows Forms 的 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658516"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="86f1b-102">逐步解說：在設計階段排列 Windows Forms 上的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="86f1b-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="86f1b-103">本文說明如何使用 Windows Forms 的版面配置功能 (例如錨定和對齊線) 來排列 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="86f1b-103">This article shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="86f1b-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="86f1b-104">Prerequisites</span></span>

<span data-ttu-id="86f1b-105">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="86f1b-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="86f1b-106">建立專案</span><span class="sxs-lookup"><span data-stu-id="86f1b-106">Create the project</span></span>

<span data-ttu-id="86f1b-107">開啟 Visual Studio, 並在 Visual Basic 或視覺效果C#中建立名為`ArrangeElementHost`的新 Windows Forms 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="86f1b-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="86f1b-108">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="86f1b-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="86f1b-109">建立 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="86f1b-109">Create the WPF control</span></span>

<span data-ttu-id="86f1b-110">在將 WPF 控制項加入專案後，即可在表單上予以排列。</span><span class="sxs-lookup"><span data-stu-id="86f1b-110">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="86f1b-111">將新的 WPF <xref:System.Windows.Controls.UserControl> 加入專案。</span><span class="sxs-lookup"><span data-stu-id="86f1b-111">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="86f1b-112">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="86f1b-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="86f1b-113">如需詳細資訊，請參閱[逐步解說：在設計階段](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)于 Windows Forms 上建立新的 WPF 內容。</span><span class="sxs-lookup"><span data-stu-id="86f1b-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="86f1b-114">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="86f1b-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="86f1b-115">在 [**屬性**] 視窗中, 將<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性的值設定為**200**。</span><span class="sxs-lookup"><span data-stu-id="86f1b-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="86f1b-116">將<xref:System.Windows.Controls.Control.Background%2A>屬性的值設定為**Blue**。</span><span class="sxs-lookup"><span data-stu-id="86f1b-116">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

5. <span data-ttu-id="86f1b-117">建置專案。</span><span class="sxs-lookup"><span data-stu-id="86f1b-117">Build the project.</span></span>

## <a name="host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="86f1b-118">在版面配置面板中裝載 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="86f1b-118">Host WPF controls in a layout panel</span></span>

<span data-ttu-id="86f1b-119">您可以使用與其他 Windows Form 控制項相同的方式，在配置面板中使用 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="86f1b-119">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

1. <span data-ttu-id="86f1b-120">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="86f1b-120">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="86f1b-121">在 [**工具箱**] 中, <xref:System.Windows.Forms.TableLayoutPanel>將控制項拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="86f1b-121">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="86f1b-122">在控制項<xref:System.Windows.Forms.TableLayoutPanel>的智慧標籤面板上, 選取 [**移除最後一個資料列**]。</span><span class="sxs-lookup"><span data-stu-id="86f1b-122">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="86f1b-123">將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更寬且更高的大小。</span><span class="sxs-lookup"><span data-stu-id="86f1b-123">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="86f1b-124">在 [**工具箱**] 中, 按兩下`UserControl1`以在<xref:System.Windows.Forms.TableLayoutPanel>控制項的第`UserControl1`一個儲存格中建立的實例。</span><span class="sxs-lookup"><span data-stu-id="86f1b-124">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="86f1b-125">`UserControl1` 的執行個體會裝載到名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="86f1b-125">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="86f1b-126">在 [**工具箱**] 中, 按兩下`UserControl1`以在<xref:System.Windows.Forms.TableLayoutPanel>控制項的第二個儲存格中建立另一個實例。</span><span class="sxs-lookup"><span data-stu-id="86f1b-126">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="86f1b-127">在 [**檔大綱**] 視窗中`tableLayoutPanel1`, 選取。</span><span class="sxs-lookup"><span data-stu-id="86f1b-127">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span>

8. <span data-ttu-id="86f1b-128">在 [**屬性**] 視窗中, 將<xref:System.Windows.Forms.Control.Padding%2A>屬性的值設定為**10、10、10、10**。</span><span class="sxs-lookup"><span data-stu-id="86f1b-128">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to **10, 10, 10, 10**.</span></span>

   <span data-ttu-id="86f1b-129">兩個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的大小會調整以配合新的配置。</span><span class="sxs-lookup"><span data-stu-id="86f1b-129">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="86f1b-130">使用對齊線來對齊 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="86f1b-130">Use snaplines to align WPF controls</span></span>

<span data-ttu-id="86f1b-131">對齊線可讓您輕鬆對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="86f1b-131">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="86f1b-132">您也可以使用對齊線來對齊 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="86f1b-132">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="86f1b-133">如需詳細資訊，請參閱[逐步解說：使用對齊線](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)排列 Windows Forms 上的控制項。</span><span class="sxs-lookup"><span data-stu-id="86f1b-133">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

1. <span data-ttu-id="86f1b-134">將的實例`UserControl1`從 [工具箱] 拖曳至表單, 並將它放在<xref:System.Windows.Forms.TableLayoutPanel>控制項下方的空間中。</span><span class="sxs-lookup"><span data-stu-id="86f1b-134">From the **Toolbox**, drag an instance of `UserControl1` onto the form, and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="86f1b-135">`UserControl1` 的執行個體會裝載到名為 `elementHost3` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="86f1b-135">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="86f1b-136">使用對齊線，將 `elementHost3` 的左邊緣與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的左邊緣對齊。</span><span class="sxs-lookup"><span data-stu-id="86f1b-136">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="86f1b-137">使用對齊線，將 `elementHost3` 的大小調整成與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項同寬。</span><span class="sxs-lookup"><span data-stu-id="86f1b-137">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="86f1b-138">將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項方向移動，直到中央對齊線出現在兩個控制項之間為止。</span><span class="sxs-lookup"><span data-stu-id="86f1b-138">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="86f1b-139">在 [**屬性**] 視窗中, 將 [Margin] 屬性的值設定為**20、20、20、20**。</span><span class="sxs-lookup"><span data-stu-id="86f1b-139">In the **Properties** window, set the value of the Margin property to **20, 20, 20, 20**.</span></span>

6. <span data-ttu-id="86f1b-140">將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項反方向移動，直到中央對齊線再度出現為止。</span><span class="sxs-lookup"><span data-stu-id="86f1b-140">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="86f1b-141">中央對齊線現在表示邊界 20。</span><span class="sxs-lookup"><span data-stu-id="86f1b-141">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="86f1b-142">向`elementHost3`右移動, 直到其左邊緣與的左邊`elementHost1`緣對齊為止。</span><span class="sxs-lookup"><span data-stu-id="86f1b-142">Move `elementHost3` to the right until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="86f1b-143">變更 `elementHost3` 的寬度，直到其右邊緣與 `elementHost2` 的右邊緣對齊為止。</span><span class="sxs-lookup"><span data-stu-id="86f1b-143">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchor-and-dock-wpf-controls"></a><span data-ttu-id="86f1b-144">錨定和停駐 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="86f1b-144">Anchor and dock WPF controls</span></span>

<span data-ttu-id="86f1b-145">裝載於表單上之 WPF 控制項的錨定和停駐行為，與其他 Windows Form 控制項相同。</span><span class="sxs-lookup"><span data-stu-id="86f1b-145">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

1. <span data-ttu-id="86f1b-146">選取 `elementHost1`。</span><span class="sxs-lookup"><span data-stu-id="86f1b-146">Select `elementHost1`.</span></span>

2. <span data-ttu-id="86f1b-147">在 [**屬性**] 視窗中, <xref:System.Windows.Forms.Control.Anchor%2A>將屬性設定為**Top、底端、Left、Right**。</span><span class="sxs-lookup"><span data-stu-id="86f1b-147">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="86f1b-148">將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更大的大小。</span><span class="sxs-lookup"><span data-stu-id="86f1b-148">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

   <span data-ttu-id="86f1b-149">`elementHost1` 控制項會調整大小以填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="86f1b-149">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="86f1b-150">選取 `elementHost2`。</span><span class="sxs-lookup"><span data-stu-id="86f1b-150">Select `elementHost2`.</span></span>

5. <span data-ttu-id="86f1b-151">在 [**屬性**] 視窗中, 將<xref:System.Windows.Forms.Control.Dock%2A>屬性的值設定為。 <xref:System.Windows.Forms.DockStyle.Fill></span><span class="sxs-lookup"><span data-stu-id="86f1b-151">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="86f1b-152">`elementHost2` 控制項會調整大小以填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="86f1b-152">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="86f1b-153">選取 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="86f1b-153">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="86f1b-154">將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Top>。</span><span class="sxs-lookup"><span data-stu-id="86f1b-154">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="86f1b-155">選取 `elementHost3`。</span><span class="sxs-lookup"><span data-stu-id="86f1b-155">Select `elementHost3`.</span></span>

9. <span data-ttu-id="86f1b-156">將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="86f1b-156">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="86f1b-157">`elementHost3` 控制項會調整大小以填滿表單上的剩餘空間。</span><span class="sxs-lookup"><span data-stu-id="86f1b-157">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="86f1b-158">調整表單的大小。</span><span class="sxs-lookup"><span data-stu-id="86f1b-158">Resize the form.</span></span>

    <span data-ttu-id="86f1b-159">這三個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項都會適當地調整大小。</span><span class="sxs-lookup"><span data-stu-id="86f1b-159">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

    <span data-ttu-id="86f1b-160">如需詳細資訊，請參閱[如何：錨定和停駐 TableLayoutPanel 控制項](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)中的子控制項。</span><span class="sxs-lookup"><span data-stu-id="86f1b-160">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86f1b-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86f1b-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="86f1b-162">如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="86f1b-162">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="86f1b-163">如何：在設計階段將控制項對齊表單邊緣</span><span class="sxs-lookup"><span data-stu-id="86f1b-163">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="86f1b-164">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="86f1b-164">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="86f1b-165">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="86f1b-165">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="86f1b-166">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="86f1b-166">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="86f1b-167">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="86f1b-167">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
