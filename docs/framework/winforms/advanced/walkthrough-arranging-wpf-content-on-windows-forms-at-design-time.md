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
ms.openlocfilehash: a8f690438136450cb12dbcf5e17ddfcca617457e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211436"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="197a3-102">逐步解說：在設計階段排列 Windows Form 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="197a3-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="197a3-103">本逐步解說示範如何使用 Windows Form 的配置功能 (例如錨定和對齊線)，來排列 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

<span data-ttu-id="197a3-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="197a3-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="197a3-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="197a3-105">Create the project.</span></span>

- <span data-ttu-id="197a3-106">建立 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-106">Create the WPF control.</span></span>

- <span data-ttu-id="197a3-107">將 WPF 控制項裝載到配置面板中。</span><span class="sxs-lookup"><span data-stu-id="197a3-107">Host WPF controls in a layout panel.</span></span>

- <span data-ttu-id="197a3-108">使用對齊線來對齊 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-108">Use snaplines to align WPF controls.</span></span>

- <span data-ttu-id="197a3-109">錨定和停駐 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-109">Anchor and dock WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="197a3-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="197a3-110">Prerequisites</span></span>

<span data-ttu-id="197a3-111">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="197a3-111">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="197a3-112">建立專案</span><span class="sxs-lookup"><span data-stu-id="197a3-112">Create the project</span></span>

<span data-ttu-id="197a3-113">開啟 Visual Studio 並建立新的 Windows Forms 應用程式專案在 Visual Basic 或 VisualC#名為`ArrangeElementHost`。</span><span class="sxs-lookup"><span data-stu-id="197a3-113">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="197a3-114">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="197a3-114">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="197a3-115">建立 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="197a3-115">Create the WPF control</span></span>

<span data-ttu-id="197a3-116">在將 WPF 控制項加入專案後，即可在表單上予以排列。</span><span class="sxs-lookup"><span data-stu-id="197a3-116">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="197a3-117">將新的 WPF <xref:System.Windows.Controls.UserControl> 加入專案。</span><span class="sxs-lookup"><span data-stu-id="197a3-117">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="197a3-118">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="197a3-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="197a3-119">如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 上的新 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="197a3-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="197a3-120">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="197a3-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="197a3-121">如需詳細資訊，請參閱[如何：選取並移動設計介面上的項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="197a3-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="197a3-122">在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。</span><span class="sxs-lookup"><span data-stu-id="197a3-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="197a3-123">將 <xref:System.Windows.Controls.Control.Background%2A> 屬性值設定為 `Blue`。</span><span class="sxs-lookup"><span data-stu-id="197a3-123">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

5. <span data-ttu-id="197a3-124">建置專案。</span><span class="sxs-lookup"><span data-stu-id="197a3-124">Build the project.</span></span>

## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="197a3-125">將 WPF 控制項裝載到配置面板中</span><span class="sxs-lookup"><span data-stu-id="197a3-125">Hosting WPF Controls in a Layout Panel</span></span>
 <span data-ttu-id="197a3-126">您可以使用與其他 Windows Form 控制項相同的方式，在配置面板中使用 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-126">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="197a3-127">將 WPF 控制項裝載到配置面板中</span><span class="sxs-lookup"><span data-stu-id="197a3-127">To host WPF controls in a layout panel</span></span>

1. <span data-ttu-id="197a3-128">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="197a3-128">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="197a3-129">在 **工具箱**，拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="197a3-129">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="197a3-130">在 <xref:System.Windows.Forms.TableLayoutPanel>控制項的智慧標籤面板中，選取**移除最後一個資料列**。</span><span class="sxs-lookup"><span data-stu-id="197a3-130">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="197a3-131">將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更寬且更高的大小。</span><span class="sxs-lookup"><span data-stu-id="197a3-131">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="197a3-132">在 **工具箱**，按兩下`UserControl1`若要建立的執行個體`UserControl1`的第一個資料格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-132">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="197a3-133">`UserControl1` 的執行個體會裝載到名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="197a3-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="197a3-134">在**工具箱**，按兩下`UserControl1`建立另一個執行個體中的第二個儲存格<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-134">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="197a3-135">在 **文件大綱**視窗中，選取`tableLayoutPanel1`。</span><span class="sxs-lookup"><span data-stu-id="197a3-135">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="197a3-136">如需詳細資訊，請參閱 <<c0> [ 文件大綱 視窗](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf)。</span><span class="sxs-lookup"><span data-stu-id="197a3-136">For more information, see [Document Outline Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span></span>

8. <span data-ttu-id="197a3-137">在 **屬性**視窗中，設定的值<xref:System.Windows.Forms.Control.Padding%2A>屬性設`10, 10, 10, 10`。</span><span class="sxs-lookup"><span data-stu-id="197a3-137">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>

     <span data-ttu-id="197a3-138">兩個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的大小會調整以配合新的配置。</span><span class="sxs-lookup"><span data-stu-id="197a3-138">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="197a3-139">使用對齊線來對齊 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="197a3-139">Using Snaplines to Align WPF Controls</span></span>
 <span data-ttu-id="197a3-140">對齊線可讓您輕鬆對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-140">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="197a3-141">您也可以使用對齊線來對齊 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-141">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="197a3-142">如需詳細資訊，請參閱[逐步解說：排列控制項，在 Windows Form 使用對齊線](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。</span><span class="sxs-lookup"><span data-stu-id="197a3-142">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="197a3-143">使用對齊線來對齊 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="197a3-143">To use snaplines to align WPF controls</span></span>

1. <span data-ttu-id="197a3-144">從**工具箱**，將拖曳的執行個體`UserControl1`拖曳至表單並將它放在下方的空間<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-144">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="197a3-145">`UserControl1` 的執行個體會裝載到名為 `elementHost3` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="197a3-145">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="197a3-146">使用對齊線，將 `elementHost3` 的左邊緣與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的左邊緣對齊。</span><span class="sxs-lookup"><span data-stu-id="197a3-146">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="197a3-147">使用對齊線，將 `elementHost3` 的大小調整成與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項同寬。</span><span class="sxs-lookup"><span data-stu-id="197a3-147">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="197a3-148">將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項方向移動，直到中央對齊線出現在兩個控制項之間為止。</span><span class="sxs-lookup"><span data-stu-id="197a3-148">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="197a3-149">在 **屬性**視窗中，將 Margin 屬性的值`20, 20, 20, 20`。</span><span class="sxs-lookup"><span data-stu-id="197a3-149">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>

6. <span data-ttu-id="197a3-150">將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項反方向移動，直到中央對齊線再度出現為止。</span><span class="sxs-lookup"><span data-stu-id="197a3-150">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="197a3-151">中央對齊線現在表示邊界 20。</span><span class="sxs-lookup"><span data-stu-id="197a3-151">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="197a3-152">將 `elementHost3` 向右移，直到其左邊緣與 `elementHost1` 的左邊緣對齊為止。</span><span class="sxs-lookup"><span data-stu-id="197a3-152">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="197a3-153">變更 `elementHost3` 的寬度，直到其右邊緣與 `elementHost2` 的右邊緣對齊為止。</span><span class="sxs-lookup"><span data-stu-id="197a3-153">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="197a3-154">錨定和停駐 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="197a3-154">Anchoring and Docking WPF Controls</span></span>
 <span data-ttu-id="197a3-155">裝載於表單上之 WPF 控制項的錨定和停駐行為，與其他 Windows Form 控制項相同。</span><span class="sxs-lookup"><span data-stu-id="197a3-155">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="197a3-156">錨定和停駐 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="197a3-156">To anchor and dock WPF controls</span></span>

1. <span data-ttu-id="197a3-157">選取 `elementHost1`。</span><span class="sxs-lookup"><span data-stu-id="197a3-157">Select `elementHost1`.</span></span>

2. <span data-ttu-id="197a3-158">在 **屬性**視窗中，將<xref:System.Windows.Forms.Control.Anchor%2A>屬性設**上、 下、 Left、 Right**。</span><span class="sxs-lookup"><span data-stu-id="197a3-158">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="197a3-159">將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更大的大小。</span><span class="sxs-lookup"><span data-stu-id="197a3-159">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

     <span data-ttu-id="197a3-160">`elementHost1` 控制項會調整大小以填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="197a3-160">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="197a3-161">選取 `elementHost2`。</span><span class="sxs-lookup"><span data-stu-id="197a3-161">Select `elementHost2`.</span></span>

5. <span data-ttu-id="197a3-162">在 **屬性**視窗中，設定的值<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="197a3-162">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="197a3-163">`elementHost2` 控制項會調整大小以填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="197a3-163">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="197a3-164">選取 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="197a3-164">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="197a3-165">將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Top>。</span><span class="sxs-lookup"><span data-stu-id="197a3-165">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="197a3-166">選取 `elementHost3`。</span><span class="sxs-lookup"><span data-stu-id="197a3-166">Select `elementHost3`.</span></span>

9. <span data-ttu-id="197a3-167">將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="197a3-167">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="197a3-168">`elementHost3` 控制項會調整大小以填滿表單上的剩餘空間。</span><span class="sxs-lookup"><span data-stu-id="197a3-168">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="197a3-169">調整表單的大小。</span><span class="sxs-lookup"><span data-stu-id="197a3-169">Resize the form.</span></span>

     <span data-ttu-id="197a3-170">這三個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項都會適當地調整大小。</span><span class="sxs-lookup"><span data-stu-id="197a3-170">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

     <span data-ttu-id="197a3-171">如需詳細資訊，請參閱[如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)。</span><span class="sxs-lookup"><span data-stu-id="197a3-171">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="197a3-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="197a3-172">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="197a3-173">如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="197a3-173">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="197a3-174">如何：將控制項和表單邊緣對齊在設計階段</span><span class="sxs-lookup"><span data-stu-id="197a3-174">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="197a3-175">逐步解說：使用對齊線的 Windows Form 上排列控制項</span><span class="sxs-lookup"><span data-stu-id="197a3-175">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="197a3-176">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="197a3-176">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="197a3-177">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="197a3-177">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="197a3-178">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="197a3-178">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
