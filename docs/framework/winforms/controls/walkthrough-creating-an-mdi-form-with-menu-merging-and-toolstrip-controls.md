---
title: 逐步解說：建立具有功能表合併和 ToolStrip 控制項的 MDI 表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: 5853760231cbece27805923c009d83e16c9b0a5e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211564"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="fcc97-102">逐步解說：建立具有功能表合併和 ToolStrip 控制項的 MDI 表單</span><span class="sxs-lookup"><span data-stu-id="fcc97-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="fcc97-103"><xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。</span><span class="sxs-lookup"><span data-stu-id="fcc97-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="fcc97-104">MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。</span><span class="sxs-lookup"><span data-stu-id="fcc97-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="fcc97-105">本逐步解說示範如何使用<xref:System.Windows.Forms.ToolStripPanel>控制項搭配 MDI 表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="fcc97-106">這個表單也支援子功能表的功能表合併。</span><span class="sxs-lookup"><span data-stu-id="fcc97-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="fcc97-107">本逐步解說會說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="fcc97-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="fcc97-108">建立 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="fcc97-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="fcc97-109">建立主功能表為您的表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-109">Creating the main menu for your form.</span></span> <span data-ttu-id="fcc97-110">[] 功能表中的實際名稱而有所不同。</span><span class="sxs-lookup"><span data-stu-id="fcc97-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="fcc97-111">新增<xref:System.Windows.Forms.ToolStripPanel>若要控制**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="fcc97-112">建立子表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-112">Creating a child form.</span></span>

- <span data-ttu-id="fcc97-113">排列<xref:System.Windows.Forms.ToolStripPanel>依 z 軸順序的控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="fcc97-114">當您完成時，您必須支援功能表合併和可移動的 MDI 表單<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="fcc97-115">若要將此主題中的程式碼複製為單一清單，請參閱[如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc97-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fcc97-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="fcc97-116">Prerequisites</span></span>

<span data-ttu-id="fcc97-117">您將需要 Visual Studio 來完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="fcc97-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="fcc97-118">建立專案</span><span class="sxs-lookup"><span data-stu-id="fcc97-118">Create the project</span></span>

1. <span data-ttu-id="fcc97-119">在 Visual Studio 中建立名為 Windows 應用程式專案**MdiForm** (**檔案** > **新增** > **專案**  > **視覺化C#** 或是**Visual Basic** > **傳統桌面** >  **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="fcc97-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="fcc97-120">在 Windows Form 設計工具中，選取的表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="fcc97-121">在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.Form.IsMdiContainer%2A>至`true`。</span><span class="sxs-lookup"><span data-stu-id="fcc97-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="fcc97-122">建立主功能表</span><span class="sxs-lookup"><span data-stu-id="fcc97-122">Create the main menu</span></span>

<span data-ttu-id="fcc97-123">MDI 父表單包含主功能表。</span><span class="sxs-lookup"><span data-stu-id="fcc97-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="fcc97-124">主功能表中有一個功能表項目名為**視窗**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="fcc97-125">具有**視窗**功能表項目，您可以建立子表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="fcc97-126">從 子表單的功能表項目會合併到主功能表中。</span><span class="sxs-lookup"><span data-stu-id="fcc97-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="fcc97-127">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="fcc97-128">新增<xref:System.Windows.Forms.ToolStripMenuItem>要<xref:System.Windows.Forms.MenuStrip>控制項並將它命名**視窗**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="fcc97-129">選取 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="fcc97-130">在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性設`ToolStripMenuItem1`。</span><span class="sxs-lookup"><span data-stu-id="fcc97-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="fcc97-131">新增至子項目的\*\* 視窗**功能表項目，然後命名子項目的**新增\*\*。</span><span class="sxs-lookup"><span data-stu-id="fcc97-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="fcc97-132">在 [屬性] 視窗中，按一下**事件**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="fcc97-133">按兩下<xref:System.Windows.Forms.ToolStripItem.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="fcc97-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="fcc97-134">Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="fcc97-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="fcc97-135">事件處理常式中插入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="fcc97-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="fcc97-136">ToolStripPanel 控制項新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="fcc97-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="fcc97-137">當您使用<xref:System.Windows.Forms.MenuStrip>控制項，您必須擁有在 MDI 表單<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="fcc97-138">您必須新增<xref:System.Windows.Forms.ToolStripPanel>若要控制**工具箱**來建置您在 Windows Form 設計工具中的 MDI 表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="fcc97-139">開啟**工具箱**，然後按一下**所有的 Windows Form**索引標籤，以顯示可用的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="fcc97-140">以滑鼠右鍵按一下以開啟捷徑功能表，然後選取**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="fcc97-141">在 [**選擇工具箱項目**] 對話方塊中，向下捲動**名稱**資料行，直到您找到**ToolStripPanel**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="fcc97-142">選取核取方塊**ToolStripPanel**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="fcc97-143"><xref:System.Windows.Forms.ToolStripPanel>控制項會出現在**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="fcc97-144">建立子表單</span><span class="sxs-lookup"><span data-stu-id="fcc97-144">Create a child form</span></span>

<span data-ttu-id="fcc97-145">在此程序中，您將定義個別的子表單類別，都有它自己<xref:System.Windows.Forms.MenuStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="fcc97-146">這種形式的功能表項目會與父表單的合併。</span><span class="sxs-lookup"><span data-stu-id="fcc97-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="fcc97-147">加入新的表單名為`ChildForm`至專案。</span><span class="sxs-lookup"><span data-stu-id="fcc97-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="fcc97-148">如需詳細資訊，請參閱[如何：將 Windows Form 加入專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="fcc97-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="fcc97-149">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>拖曳至子表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="fcc97-150">按一下 <xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 （glyph) (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**編輯項目**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-150">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="fcc97-151">在 **項目集合編輯器**對話方塊方塊中，加入新<xref:System.Windows.Forms.ToolStripMenuItem>名為**ChildMenuItem**子功能表。</span><span class="sxs-lookup"><span data-stu-id="fcc97-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="fcc97-152">如需詳細資訊，請參閱 < [ToolStrip 項目集合編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="fcc97-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="fcc97-153">測試表單</span><span class="sxs-lookup"><span data-stu-id="fcc97-153">Test the form</span></span>

1. <span data-ttu-id="fcc97-154">按下**F5**編譯及執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="fcc97-155">按一下 [ **] 視窗**以開啟功能表，然後按一下功能表項目**新增**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="fcc97-156">表單的 MDI 工作區中建立新的子表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="fcc97-157">在主功能表會合併子表單的功能表。</span><span class="sxs-lookup"><span data-stu-id="fcc97-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="fcc97-158">關閉子表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-158">Close the child form.</span></span>

     <span data-ttu-id="fcc97-159">從主功能表中，移除子表單的功能表。</span><span class="sxs-lookup"><span data-stu-id="fcc97-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="fcc97-160">按一下 **新增**數次。</span><span class="sxs-lookup"><span data-stu-id="fcc97-160">Click **New** several times.</span></span>

     <span data-ttu-id="fcc97-161">子表單並自動列底下\*\* 視窗\*\*功能表項目，因為<xref:System.Windows.Forms.MenuStrip>控制項的<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性指派。</span><span class="sxs-lookup"><span data-stu-id="fcc97-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="fcc97-162">加入 ToolStrip 的支援</span><span class="sxs-lookup"><span data-stu-id="fcc97-162">Add ToolStrip support</span></span>

<span data-ttu-id="fcc97-163">在此程序中，您會將四個<xref:System.Windows.Forms.ToolStrip>MDI 父表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="fcc97-164">每個<xref:System.Windows.Forms.ToolStrip>控制項會加入內<xref:System.Windows.Forms.ToolStripPanel>控制項停駐在表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="fcc97-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="fcc97-165">從**工具箱**，拖曳<xref:System.Windows.Forms.ToolStripPanel>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="fcc97-166">具有<xref:System.Windows.Forms.ToolStripPanel>選取控制項中，按兩下<xref:System.Windows.Forms.ToolStrip>控制中**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="fcc97-167">A<xref:System.Windows.Forms.ToolStrip>控制項建立<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="fcc97-168">選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="fcc97-169">在 [屬性] 視窗中，變更控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Left>。</span><span class="sxs-lookup"><span data-stu-id="fcc97-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="fcc97-170"><xref:System.Windows.Forms.ToolStripPanel>控制項停駐在主功能表下的表單的左邊。</span><span class="sxs-lookup"><span data-stu-id="fcc97-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="fcc97-171">在 MDI 工作區調整大小以配合<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="fcc97-172">重複步驟 1 到 4。</span><span class="sxs-lookup"><span data-stu-id="fcc97-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="fcc97-173">新的停駐<xref:System.Windows.Forms.ToolStripPanel>表單頂端的控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="fcc97-174"><xref:System.Windows.Forms.ToolStripPanel>主功能表下，但右邊的第一個控制項所停駐<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="fcc97-175">此步驟說明如何在正確位置中的疊置順序的重要性<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="fcc97-176">重複步驟 1 到 4 的另外兩個<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="fcc97-177">新的停駐<xref:System.Windows.Forms.ToolStripPanel>到右邊，並在表單底部的控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="fcc97-178">ToolStripPanel 控制項依 z 軸順序排列</span><span class="sxs-lookup"><span data-stu-id="fcc97-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="fcc97-179">停駐的位置<xref:System.Windows.Forms.ToolStripPanel>MDI 表單上的控制項由控制項的疊置順序位置。</span><span class="sxs-lookup"><span data-stu-id="fcc97-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="fcc97-180">您可以輕易地排列控制項在文件大綱 視窗中的 z-order。</span><span class="sxs-lookup"><span data-stu-id="fcc97-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="fcc97-181">在 **檢視** 功能表中，按一下**其他 Windows**，然後按一下 **文件大綱**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="fcc97-182">排列方式您<xref:System.Windows.Forms.ToolStripPanel>控制項從上一個程序並非標準用法。</span><span class="sxs-lookup"><span data-stu-id="fcc97-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="fcc97-183">這是因為疊置順序不正確。</span><span class="sxs-lookup"><span data-stu-id="fcc97-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="fcc97-184">您可以使用 [文件大綱] 視窗來變更控制項疊置順序。</span><span class="sxs-lookup"><span data-stu-id="fcc97-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="fcc97-185">在 [文件大綱] 視窗中，選取**ToolStripPanel4**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="fcc97-186">按一下向下箭頭按鈕重複，直到**ToolStripPanel4**位於清單底部。</span><span class="sxs-lookup"><span data-stu-id="fcc97-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="fcc97-187">**ToolStripPanel4**控制項所停駐到其他控制項下的表單底部。</span><span class="sxs-lookup"><span data-stu-id="fcc97-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="fcc97-188">選取  **ToolStripPanel2**。</span><span class="sxs-lookup"><span data-stu-id="fcc97-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="fcc97-189">控制項第三個位置清單中按一下向下箭頭按鈕一次。</span><span class="sxs-lookup"><span data-stu-id="fcc97-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="fcc97-190">**ToolStripPanel2**控制項停駐在表單中，主功能表下方以及高於其他控制項的頂端。</span><span class="sxs-lookup"><span data-stu-id="fcc97-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="fcc97-191">選取不同的控制項中**文件大綱**視窗並將其移到疊置順序的不同位置。</span><span class="sxs-lookup"><span data-stu-id="fcc97-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="fcc97-192">請注意位置停駐控制項的疊置順序的影響。</span><span class="sxs-lookup"><span data-stu-id="fcc97-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="fcc97-193">使用 CTRL-Z 或**恢復**上**編輯**功能表來復原您的變更。</span><span class="sxs-lookup"><span data-stu-id="fcc97-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="fcc97-194">檢查點-測試您的表單</span><span class="sxs-lookup"><span data-stu-id="fcc97-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="fcc97-195">按下**F5**編譯及執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="fcc97-196">按 的底框<xref:System.Windows.Forms.ToolStrip>控制項，並在表單上，將控制項拖曳至不同的位置。</span><span class="sxs-lookup"><span data-stu-id="fcc97-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="fcc97-197">您可以拖曳<xref:System.Windows.Forms.ToolStrip>控制項從某個<xref:System.Windows.Forms.ToolStripPanel>到另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="fcc97-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fcc97-198">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fcc97-198">Next steps</span></span>

<span data-ttu-id="fcc97-199">在本逐步解說中，您已建立 MDI 父表單與<xref:System.Windows.Forms.ToolStrip>控制項和功能表合併。</span><span class="sxs-lookup"><span data-stu-id="fcc97-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="fcc97-200">您可以使用<xref:System.Windows.Forms.ToolStrip>用於許多其他用途的控制項系列：</span><span class="sxs-lookup"><span data-stu-id="fcc97-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="fcc97-201">建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="fcc97-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="fcc97-202">如需詳細資訊，請參閱 < [ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc97-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="fcc97-203">使用自動填入的標準功能表中建立的表單。</span><span class="sxs-lookup"><span data-stu-id="fcc97-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="fcc97-204">如需詳細資訊，請參閱[逐步解說：對表單提供標準功能表項目](walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc97-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="fcc97-205">提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。</span><span class="sxs-lookup"><span data-stu-id="fcc97-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="fcc97-206">如需詳細資訊，請參閱[如何：設定應用程式的 ToolStrip 產生器](how-to-set-the-toolstrip-renderer-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc97-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcc97-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcc97-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="fcc97-208">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="fcc97-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="fcc97-209">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="fcc97-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="fcc97-210">如何：將 MenuStrip 插入至 MDI 下拉式功能表</span><span class="sxs-lookup"><span data-stu-id="fcc97-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="fcc97-211">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="fcc97-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
