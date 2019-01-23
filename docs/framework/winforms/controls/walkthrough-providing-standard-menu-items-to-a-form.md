---
title: 逐步解說：對表單提供標準功能表項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: b0f88f8c28b613b9eae580c851ee4dd1282e77e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505103"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="80419-102">逐步解說：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="80419-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="80419-103">您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。</span><span class="sxs-lookup"><span data-stu-id="80419-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="80419-104">本逐步解說示範如何使用<xref:System.Windows.Forms.MenuStrip>控制項來建立標準功能表。</span><span class="sxs-lookup"><span data-stu-id="80419-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="80419-105">當使用者選取功能表項目，也會回應格式。</span><span class="sxs-lookup"><span data-stu-id="80419-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="80419-106">本逐步解說會說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="80419-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="80419-107">建立 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="80419-107">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="80419-108">建立標準功能表。</span><span class="sxs-lookup"><span data-stu-id="80419-108">Creating a standard menu.</span></span>  
  
-   <span data-ttu-id="80419-109">建立<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="80419-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
-   <span data-ttu-id="80419-110">處理功能表項目選取項目。</span><span class="sxs-lookup"><span data-stu-id="80419-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="80419-111">當您完成時，您必須具有標準功能表會顯示功能表項目中的選取項目表單<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="80419-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="80419-112">若要複製一份清單列出本主題中的程式碼，請參閱[How to:對表單提供標準功能表項目](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="80419-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80419-113">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="80419-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="80419-114">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="80419-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="80419-115">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="80419-115">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="80419-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="80419-116">Prerequisites</span></span>  
 <span data-ttu-id="80419-117">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="80419-117">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="80419-118">若要能夠建立和安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="80419-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="80419-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="80419-119">Creating the Project</span></span>  
 <span data-ttu-id="80419-120">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="80419-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="80419-121">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="80419-121">To create the project</span></span>  
  
1.  <span data-ttu-id="80419-122">建立 Windows 應用程式專案，稱為**StandardMenuForm** (**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Form應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="80419-122">Create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="80419-123">在 Windows Form 設計工具中，選取的表單。</span><span class="sxs-lookup"><span data-stu-id="80419-123">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="80419-124">建立標準功能表</span><span class="sxs-lookup"><span data-stu-id="80419-124">Creating a Standard Menu</span></span>  
 <span data-ttu-id="80419-125">Windows Form 設計工具可以自動填入<xref:System.Windows.Forms.MenuStrip>具有標準功能表項目控制項。</span><span class="sxs-lookup"><span data-stu-id="80419-125">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="80419-126">建立標準功能表</span><span class="sxs-lookup"><span data-stu-id="80419-126">To create a standard menu</span></span>  
  
1.  <span data-ttu-id="80419-127">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="80419-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2.  <span data-ttu-id="80419-128">按一下 <xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 （glyph) (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**插入標準項目**。</span><span class="sxs-lookup"><span data-stu-id="80419-128">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="80419-129"><xref:System.Windows.Forms.MenuStrip>控制項填入標準功能表項目。</span><span class="sxs-lookup"><span data-stu-id="80419-129">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3.  <span data-ttu-id="80419-130">按一下 **檔案**功能表項目，以查看其預設功能表項目和對應的圖示。</span><span class="sxs-lookup"><span data-stu-id="80419-130">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="80419-131">建立 StatusStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="80419-131">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="80419-132">使用<xref:System.Windows.Forms.StatusStrip>控制項來顯示 Windows Forms 應用程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="80419-132">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="80419-133">在目前的範例中，使用者所選取的功能表項目會顯示在<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="80419-133">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="80419-134">若要建立 StatusStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="80419-134">To create a StatusStrip control</span></span>  
  
1.  <span data-ttu-id="80419-135">從**工具箱**，拖曳<xref:System.Windows.Forms.StatusStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="80419-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="80419-136"><xref:System.Windows.Forms.StatusStrip>控制項自動停駐於表單底部。</span><span class="sxs-lookup"><span data-stu-id="80419-136">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2.  <span data-ttu-id="80419-137">按一下 <xref:System.Windows.Forms.StatusStrip>控制項的下拉式按鈕，然後選取**statuslabel 設**以新增<xref:System.Windows.Forms.ToolStripStatusLabel>若要控制<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="80419-137">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="80419-138">處理項目選取</span><span class="sxs-lookup"><span data-stu-id="80419-138">Handling Item Selection</span></span>  
 <span data-ttu-id="80419-139">處理<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件以回應使用者選取功能表項目時。</span><span class="sxs-lookup"><span data-stu-id="80419-139">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="80419-140">若要處理的項目選取</span><span class="sxs-lookup"><span data-stu-id="80419-140">To handle item selection</span></span>  
  
1.  <span data-ttu-id="80419-141">按一下 **檔案**功能表項目，您在 「 建立中建立標準功能表一節。</span><span class="sxs-lookup"><span data-stu-id="80419-141">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2.  <span data-ttu-id="80419-142">在 [屬性] 視窗中按一下 [事件]。</span><span class="sxs-lookup"><span data-stu-id="80419-142">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="80419-143">按兩下<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。</span><span class="sxs-lookup"><span data-stu-id="80419-143">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="80419-144">Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。</span><span class="sxs-lookup"><span data-stu-id="80419-144">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4.  <span data-ttu-id="80419-145">事件處理常式中插入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="80419-145">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  <span data-ttu-id="80419-146">插入`UpdateStatus`在表單的公用程式方法定義。</span><span class="sxs-lookup"><span data-stu-id="80419-146">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="80419-147">檢查點</span><span class="sxs-lookup"><span data-stu-id="80419-147">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="80419-148">若要測試您的表單</span><span class="sxs-lookup"><span data-stu-id="80419-148">To test your form</span></span>  
  
1.  <span data-ttu-id="80419-149">按 F5 以編譯並執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="80419-149">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="80419-150">按一下 **檔案**以開啟功能表的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="80419-150">Click the **File** menu item to open the menu.</span></span>  
  
3.  <span data-ttu-id="80419-151">在 [**檔案**] 功能表中，按一下其中一個項目，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="80419-151">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="80419-152"><xref:System.Windows.Forms.StatusStrip>控制項會顯示選取的項目。</span><span class="sxs-lookup"><span data-stu-id="80419-152">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="80419-153">後續步驟</span><span class="sxs-lookup"><span data-stu-id="80419-153">Next Steps</span></span>  
 <span data-ttu-id="80419-154">在本逐步解說中，您已建立具有標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="80419-154">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="80419-155">您可以使用<xref:System.Windows.Forms.ToolStrip>用於許多其他用途的控制項系列：</span><span class="sxs-lookup"><span data-stu-id="80419-155">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="80419-156">建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="80419-156">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="80419-157">如需詳細資訊，請參閱 < [ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="80419-157">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="80419-158">建立多個文件介面 (MDI) 表單使用停駐<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="80419-158">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="80419-159">如需詳細資訊，請參閱[逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="80419-159">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
-   <span data-ttu-id="80419-160">提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。</span><span class="sxs-lookup"><span data-stu-id="80419-160">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="80419-161">如需詳細資訊，請參閱[＜How to：設定應用程式的 ToolStrip 產生器](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="80419-161">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80419-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80419-162">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="80419-163">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="80419-163">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
