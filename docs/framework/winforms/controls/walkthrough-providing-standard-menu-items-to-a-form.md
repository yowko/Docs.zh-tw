---
title: "逐步解說：對表單提供標準功能表項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89089617a62ab079dd4cccf3ddf6e1e774bac8ba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="66f22-102">逐步解說：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="66f22-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="66f22-103">您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。</span><span class="sxs-lookup"><span data-stu-id="66f22-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="66f22-104">本逐步解說示範如何使用<xref:System.Windows.Forms.MenuStrip>控制項來建立標準功能表。</span><span class="sxs-lookup"><span data-stu-id="66f22-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="66f22-105">當使用者選取功能表項目，也會回應表單。</span><span class="sxs-lookup"><span data-stu-id="66f22-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="66f22-106">在本逐步解說說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="66f22-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="66f22-107">建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="66f22-107">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="66f22-108">建立標準功能表。</span><span class="sxs-lookup"><span data-stu-id="66f22-108">Creating a standard menu.</span></span>  
  
-   <span data-ttu-id="66f22-109">建立<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="66f22-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
-   <span data-ttu-id="66f22-110">處理功能表項目選取項目。</span><span class="sxs-lookup"><span data-stu-id="66f22-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="66f22-111">當您完成時，您必須具有標準功能表會顯示功能表項目中的選取項目表單<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="66f22-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="66f22-112">若要為單一列出本主題中複製的程式碼，請參閱[How to： 提供標準功能表項目表單](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="66f22-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66f22-113">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="66f22-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="66f22-114">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="66f22-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="66f22-115">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="66f22-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="66f22-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="66f22-116">Prerequisites</span></span>  
 <span data-ttu-id="66f22-117">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="66f22-117">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="66f22-118">若要能夠建立和執行 Windows Form 應用程式專案的電腦上有足夠的權限所在[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="66f22-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="66f22-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="66f22-119">Creating the Project</span></span>  
 <span data-ttu-id="66f22-120">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="66f22-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="66f22-121">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="66f22-121">To create the project</span></span>  
  
1.  <span data-ttu-id="66f22-122">建立 Windows 應用程式專案，稱為**StandardMenuForm**。</span><span class="sxs-lookup"><span data-stu-id="66f22-122">Create a Windows application project called **StandardMenuForm**.</span></span>  
  
     <span data-ttu-id="66f22-123">如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="66f22-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="66f22-124">在 Windows Form 設計工具中，選取的表單。</span><span class="sxs-lookup"><span data-stu-id="66f22-124">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="66f22-125">建立標準功能表</span><span class="sxs-lookup"><span data-stu-id="66f22-125">Creating a Standard Menu</span></span>  
 <span data-ttu-id="66f22-126">Windows Form 設計工具可以自動填入<xref:System.Windows.Forms.MenuStrip>具有標準功能表項目控制項。</span><span class="sxs-lookup"><span data-stu-id="66f22-126">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="66f22-127">建立標準功能表</span><span class="sxs-lookup"><span data-stu-id="66f22-127">To create a standard menu</span></span>  
  
1.  <span data-ttu-id="66f22-128">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="66f22-128">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2.  <span data-ttu-id="66f22-129">按一下<xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 並選取**插入標準項目**。</span><span class="sxs-lookup"><span data-stu-id="66f22-129">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="66f22-130"><xref:System.Windows.Forms.MenuStrip>標準功能表項目填入控制項。</span><span class="sxs-lookup"><span data-stu-id="66f22-130">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3.  <span data-ttu-id="66f22-131">按一下**檔案**功能表項目即可查看其預設功能表項目和對應的圖示。</span><span class="sxs-lookup"><span data-stu-id="66f22-131">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="66f22-132">建立 StatusStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="66f22-132">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="66f22-133">使用<xref:System.Windows.Forms.StatusStrip>控制項來顯示 Windows Form 應用程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="66f22-133">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="66f22-134">在目前的範例中，使用者所選取的功能表項目都會顯示在<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="66f22-134">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="66f22-135">若要建立 StatusStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="66f22-135">To create a StatusStrip control</span></span>  
  
1.  <span data-ttu-id="66f22-136">從**工具箱**，拖曳<xref:System.Windows.Forms.StatusStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="66f22-136">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="66f22-137"><xref:System.Windows.Forms.StatusStrip>控制項自動停駐於表單的下方。</span><span class="sxs-lookup"><span data-stu-id="66f22-137">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2.  <span data-ttu-id="66f22-138">按一下<xref:System.Windows.Forms.StatusStrip>控制項的下拉式按鈕，然後選取**statuslabel 設**新增<xref:System.Windows.Forms.ToolStripStatusLabel>控制權傳輸至<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="66f22-138">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="66f22-139">處理的項目選取</span><span class="sxs-lookup"><span data-stu-id="66f22-139">Handling Item Selection</span></span>  
 <span data-ttu-id="66f22-140">處理<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件回應使用者選取功能表項目時。</span><span class="sxs-lookup"><span data-stu-id="66f22-140">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="66f22-141">若要處理的項目選取</span><span class="sxs-lookup"><span data-stu-id="66f22-141">To handle item selection</span></span>  
  
1.  <span data-ttu-id="66f22-142">按一下**檔案**功能表項目，您在 「 建立標準功能表區段。</span><span class="sxs-lookup"><span data-stu-id="66f22-142">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2.  <span data-ttu-id="66f22-143">在**屬性**視窗中，按一下 **事件**。</span><span class="sxs-lookup"><span data-stu-id="66f22-143">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="66f22-144">按兩下<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。</span><span class="sxs-lookup"><span data-stu-id="66f22-144">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="66f22-145">Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。</span><span class="sxs-lookup"><span data-stu-id="66f22-145">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4.  <span data-ttu-id="66f22-146">此事件處理常式中插入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="66f22-146">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  <span data-ttu-id="66f22-147">插入`UpdateStatus`至表單的公用程式方法定義。</span><span class="sxs-lookup"><span data-stu-id="66f22-147">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="66f22-148">檢查點</span><span class="sxs-lookup"><span data-stu-id="66f22-148">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="66f22-149">若要測試您的表單</span><span class="sxs-lookup"><span data-stu-id="66f22-149">To test your form</span></span>  
  
1.  <span data-ttu-id="66f22-150">按 F5 編譯和執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="66f22-150">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="66f22-151">按一下**檔案**開啟功能表的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="66f22-151">Click the **File** menu item to open the menu.</span></span>  
  
3.  <span data-ttu-id="66f22-152">在**檔案**功能表上，按一下其中一個項目，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="66f22-152">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="66f22-153"><xref:System.Windows.Forms.StatusStrip>控制項會顯示選取的項目。</span><span class="sxs-lookup"><span data-stu-id="66f22-153">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="66f22-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="66f22-154">Next Steps</span></span>  
 <span data-ttu-id="66f22-155">在本逐步解說中，您已建立具有標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="66f22-155">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="66f22-156">您可以使用<xref:System.Windows.Forms.ToolStrip>系列用於許多其他用途的控制項：</span><span class="sxs-lookup"><span data-stu-id="66f22-156">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="66f22-157">建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="66f22-157">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="66f22-158">如需詳細資訊，請參閱[ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="66f22-158">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="66f22-159">建立多個文件介面 (MDI) 表單上具有停駐<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="66f22-159">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="66f22-160">如需詳細資訊，請參閱[逐步解說： 使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="66f22-160">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
-   <span data-ttu-id="66f22-161">提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。</span><span class="sxs-lookup"><span data-stu-id="66f22-161">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="66f22-162">如需詳細資訊，請參閱[How to： 設定應用程式的 ToolStrip 產生器](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="66f22-162">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f22-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="66f22-163">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="66f22-164">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="66f22-164">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
