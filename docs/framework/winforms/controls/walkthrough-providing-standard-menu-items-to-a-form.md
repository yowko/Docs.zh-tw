---
title: 逐步解說：向表單提供標準的功能表項目
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
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211509"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="c9f6e-102">逐步解說：向表單提供標準的功能表項目</span><span class="sxs-lookup"><span data-stu-id="c9f6e-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="c9f6e-103">您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="c9f6e-104">本逐步解說示範如何使用<xref:System.Windows.Forms.MenuStrip>控制項來建立標準功能表。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="c9f6e-105">當使用者選取功能表項目，也會回應格式。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="c9f6e-106">本逐步解說會說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="c9f6e-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="c9f6e-107">建立 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="c9f6e-108">建立標準功能表。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-108">Creating a standard menu.</span></span>

- <span data-ttu-id="c9f6e-109">建立<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="c9f6e-110">處理功能表項目選取項目。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-110">Handling menu item selection.</span></span>

<span data-ttu-id="c9f6e-111">當您完成時，您必須具有標準功能表會顯示功能表項目中的選取項目表單<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="c9f6e-112">若要將此主題中的程式碼複製為單一清單，請參閱[如何：對表單提供標準功能表項目](how-to-provide-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c9f6e-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="c9f6e-113">Prerequisites</span></span>

<span data-ttu-id="c9f6e-114">您將需要 Visual Studio 來完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c9f6e-115">建立專案</span><span class="sxs-lookup"><span data-stu-id="c9f6e-115">Create the project</span></span>

1. <span data-ttu-id="c9f6e-116">在 Visual Studio 中建立名為 Windows 應用程式專案**StandardMenuForm** (**檔案** > **新增** > **專案**  > **視覺化C#** 或是**Visual Basic** > **傳統桌面** >  **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="c9f6e-117">在 Windows Form 設計工具中，選取的表單。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="c9f6e-118">建立標準功能表</span><span class="sxs-lookup"><span data-stu-id="c9f6e-118">Create a standard menu</span></span>

<span data-ttu-id="c9f6e-119">Windows Form 設計工具可以自動填入<xref:System.Windows.Forms.MenuStrip>具有標準功能表項目控制項。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="c9f6e-120">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="c9f6e-121">按一下 <xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 （glyph) (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**插入標準項目**。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-121">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="c9f6e-122"><xref:System.Windows.Forms.MenuStrip>控制項填入標準功能表項目。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="c9f6e-123">按一下 **檔案**功能表項目，以查看其預設功能表項目和對應的圖示。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="c9f6e-124">建立 StatusStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="c9f6e-124">Create a StatusStrip control</span></span>

<span data-ttu-id="c9f6e-125">使用<xref:System.Windows.Forms.StatusStrip>控制項來顯示 Windows Forms 應用程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="c9f6e-126">在目前的範例中，使用者所選取的功能表項目會顯示在<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="c9f6e-127">從**工具箱**，拖曳<xref:System.Windows.Forms.StatusStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="c9f6e-128"><xref:System.Windows.Forms.StatusStrip>控制項自動停駐於表單底部。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="c9f6e-129">按一下 <xref:System.Windows.Forms.StatusStrip>控制項的下拉式按鈕，然後選取**statuslabel 設**以新增<xref:System.Windows.Forms.ToolStripStatusLabel>若要控制<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="c9f6e-130">處理項目選取</span><span class="sxs-lookup"><span data-stu-id="c9f6e-130">Handle item selection</span></span>

<span data-ttu-id="c9f6e-131">處理<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件以回應使用者選取功能表項目時。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="c9f6e-132">按一下 **檔案**功能表項目，您在 「 建立中建立標準功能表一節。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="c9f6e-133">在 [屬性] 視窗中按一下 [事件]。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="c9f6e-134">按兩下<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="c9f6e-135">Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="c9f6e-136">事件處理常式中插入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="c9f6e-137">插入`UpdateStatus`在表單的公用程式方法定義。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="c9f6e-138">檢查點-測試您的表單</span><span class="sxs-lookup"><span data-stu-id="c9f6e-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="c9f6e-139">按下**F5**編譯及執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="c9f6e-140">按一下 **檔案**以開啟功能表的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="c9f6e-141">在 [**檔案**] 功能表中，按一下其中一個項目，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="c9f6e-142"><xref:System.Windows.Forms.StatusStrip>控制項會顯示選取的項目。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c9f6e-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c9f6e-143">Next steps</span></span>

<span data-ttu-id="c9f6e-144">在本逐步解說中，您已建立具有標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="c9f6e-145">您可以使用<xref:System.Windows.Forms.ToolStrip>用於許多其他用途的控制項系列：</span><span class="sxs-lookup"><span data-stu-id="c9f6e-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="c9f6e-146">建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="c9f6e-147">如需詳細資訊，請參閱 < [ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="c9f6e-148">建立多個文件介面 (MDI) 表單使用停駐<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="c9f6e-149">如需詳細資訊，請參閱[逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="c9f6e-150">提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="c9f6e-151">如需詳細資訊，請參閱[如何：設定應用程式的 ToolStrip 產生器](how-to-set-the-toolstrip-renderer-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f6e-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9f6e-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9f6e-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="c9f6e-153">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="c9f6e-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
