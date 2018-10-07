---
title: 逐步解說：在設計階段排列 Windows Form 的 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 062b9b943d187ccd4105f3772688c563f540d696
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846470"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="e9f3d-102">逐步解說：在設計階段排列 Windows Form 的 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="e9f3d-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="e9f3d-103">本逐步解說示範如何使用 Windows Form 的配置功能 (例如錨定和對齊線)，來排列 Windows Presentation Foundation (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

 <span data-ttu-id="e9f3d-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="e9f3d-104">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="e9f3d-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-105">Create the project.</span></span>

-   <span data-ttu-id="e9f3d-106">建立 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-106">Create the WPF control.</span></span>

-   <span data-ttu-id="e9f3d-107">將 WPF 控制項裝載到配置面板中。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-107">Host WPF controls in a layout panel.</span></span>

-   <span data-ttu-id="e9f3d-108">使用對齊線來對齊 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-108">Use snaplines to align WPF controls.</span></span>

-   <span data-ttu-id="e9f3d-109">錨定和停駐 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-109">Anchor and dock WPF controls.</span></span>

> [!NOTE]
>  <span data-ttu-id="e9f3d-110">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e9f3d-111">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e9f3d-112">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e9f3d-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="e9f3d-113">Prerequisites</span></span>  
 <span data-ttu-id="e9f3d-114">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="e9f3d-114">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="e9f3d-115">Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-115">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="e9f3d-116">建立專案</span><span class="sxs-lookup"><span data-stu-id="e9f3d-116">Creating the Project</span></span>  
 <span data-ttu-id="e9f3d-117">第一個步驟是建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9f3d-118">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="e9f3d-119">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="e9f3d-119">To create the project</span></span>  
  
-   <span data-ttu-id="e9f3d-120">建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`ArrangeElementHost`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="e9f3d-121">建立 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="e9f3d-122">在將 WPF 控制項加入專案後，即可在表單上予以排列。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="e9f3d-123">建立 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-123">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="e9f3d-124">將新的 WPF <xref:System.Windows.Controls.UserControl> 加入專案。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="e9f3d-125">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="e9f3d-126">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 建立新 WPF 內容在設計階段的 Windows Form 上](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="e9f3d-127">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="e9f3d-128">如需詳細資訊，請參閱 <<c0> [ 如何： 選取和移動設計介面上的項目](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474)。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-128">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="e9f3d-129">在 **屬性**視窗中，設定的值<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>屬性，以`200`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="e9f3d-130">將 <xref:System.Windows.Controls.Control.Background%2A> 屬性值設定為 `Blue`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5.  <span data-ttu-id="e9f3d-131">建置專案。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="e9f3d-132">將 WPF 控制項裝載到配置面板中</span><span class="sxs-lookup"><span data-stu-id="e9f3d-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="e9f3d-133">您可以使用與其他 Windows Form 控制項相同的方式，在配置面板中使用 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="e9f3d-134">將 WPF 控制項裝載到配置面板中</span><span class="sxs-lookup"><span data-stu-id="e9f3d-134">To host WPF controls in a layout panel</span></span>  
  
1.  <span data-ttu-id="e9f3d-135">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="e9f3d-136">在 **工具箱**，拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3.  <span data-ttu-id="e9f3d-137">在 <xref:System.Windows.Forms.TableLayoutPanel>控制項的智慧標籤面板中，選取**移除最後一個資料列**。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4.  <span data-ttu-id="e9f3d-138">將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更寬且更高的大小。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5.  <span data-ttu-id="e9f3d-139">在 **工具箱**，按兩下`UserControl1`若要建立的執行個體`UserControl1`的第一個資料格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="e9f3d-140">`UserControl1` 的執行個體會裝載到名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6.  <span data-ttu-id="e9f3d-141">在**工具箱**，按兩下`UserControl1`建立另一個執行個體中的第二個儲存格<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="e9f3d-142">在 **文件大綱**視窗中，選取`tableLayoutPanel1`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="e9f3d-143">如需詳細資訊，請參閱 <<c0> [ 文件大綱 視窗](https://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8)。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-143">For more information, see [Document Outline Window](https://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span></span>  
  
8.  <span data-ttu-id="e9f3d-144">在 **屬性**視窗中，設定的值<xref:System.Windows.Forms.Control.Padding%2A>屬性設`10, 10, 10, 10`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="e9f3d-145">兩個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的大小會調整以配合新的配置。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="e9f3d-146">使用對齊線來對齊 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="e9f3d-147">對齊線可讓您輕鬆對齊表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="e9f3d-148">您也可以使用對齊線來對齊 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="e9f3d-149">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 在 Windows Form 使用對齊線排列的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="e9f3d-150">使用對齊線來對齊 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-150">To use snaplines to align WPF controls</span></span>  
  
1.  <span data-ttu-id="e9f3d-151">從**工具箱**，將拖曳的執行個體`UserControl1`拖曳至表單並將它放在下方的空間<xref:System.Windows.Forms.TableLayoutPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="e9f3d-152">`UserControl1` 的執行個體會裝載到名為 `elementHost3` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2.  <span data-ttu-id="e9f3d-153">使用對齊線，將 `elementHost3` 的左邊緣與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的左邊緣對齊。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="e9f3d-154">使用對齊線，將 `elementHost3` 的大小調整成與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項同寬。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="e9f3d-155">將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項方向移動，直到中央對齊線出現在兩個控制項之間為止。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5.  <span data-ttu-id="e9f3d-156">在 **屬性**視窗中，將 Margin 屬性的值`20, 20, 20, 20`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6.  <span data-ttu-id="e9f3d-157">將 `elementHost3` 往 <xref:System.Windows.Forms.TableLayoutPanel> 控制項反方向移動，直到中央對齊線再度出現為止。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="e9f3d-158">中央對齊線現在表示邊界 20。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-158">The center snapline now indicates a margin of 20.</span></span>  
  
7.  <span data-ttu-id="e9f3d-159">將 `elementHost3` 向右移，直到其左邊緣與 `elementHost1` 的左邊緣對齊為止。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8.  <span data-ttu-id="e9f3d-160">變更 `elementHost3` 的寬度，直到其右邊緣與 `elementHost2` 的右邊緣對齊為止。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="e9f3d-161">錨定和停駐 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="e9f3d-162">裝載於表單上之 WPF 控制項的錨定和停駐行為，與其他 Windows Form 控制項相同。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="e9f3d-163">錨定和停駐 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-163">To anchor and dock WPF controls</span></span>  
  
1.  <span data-ttu-id="e9f3d-164">選取 `elementHost1`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-164">Select `elementHost1`.</span></span>  
  
2.  <span data-ttu-id="e9f3d-165">在 **屬性**視窗中，將<xref:System.Windows.Forms.Control.Anchor%2A>屬性設**上、 下、 Left、 Right**。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3.  <span data-ttu-id="e9f3d-166">將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小調整為更大的大小。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="e9f3d-167">`elementHost1` 控制項會調整大小以填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4.  <span data-ttu-id="e9f3d-168">選取 `elementHost2`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-168">Select `elementHost2`.</span></span>  
  
5.  <span data-ttu-id="e9f3d-169">在 **屬性**視窗中，設定的值<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="e9f3d-170">`elementHost2` 控制項會調整大小以填滿儲存格。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6.  <span data-ttu-id="e9f3d-171">選取 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="e9f3d-172">將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Top>。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8.  <span data-ttu-id="e9f3d-173">選取 `elementHost3`。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="e9f3d-174">將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="e9f3d-175">`elementHost3` 控制項會調整大小以填滿表單上的剩餘空間。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="e9f3d-176">調整表單的大小。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-176">Resize the form.</span></span>  
  
     <span data-ttu-id="e9f3d-177">這三個 <xref:System.Windows.Forms.Integration.ElementHost> 控制項都會適當地調整大小。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="e9f3d-178">如需詳細資訊，請參閱 <<c0> [ 如何： 錨定和停駐 TableLayoutPanel 控制項中的子控制項](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f3d-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f3d-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9f3d-179">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="e9f3d-180">操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="e9f3d-181">操作說明：在設計階段將控制項對齊表單邊緣</span><span class="sxs-lookup"><span data-stu-id="e9f3d-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="e9f3d-182">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="e9f3d-183">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="e9f3d-183">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="e9f3d-184">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="e9f3d-184">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="e9f3d-185">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="e9f3d-185">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
