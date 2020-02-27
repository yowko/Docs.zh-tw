---
title: 逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單
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
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628783"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="07ae1-102">逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單</span><span class="sxs-lookup"><span data-stu-id="07ae1-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="07ae1-103"><xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。</span><span class="sxs-lookup"><span data-stu-id="07ae1-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="07ae1-104">MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。</span><span class="sxs-lookup"><span data-stu-id="07ae1-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="07ae1-105">本逐步解說示範如何搭配使用 <xref:System.Windows.Forms.ToolStripPanel> 控制項與 MDI 表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="07ae1-106">這個表單也支援子功能表的功能表合併。</span><span class="sxs-lookup"><span data-stu-id="07ae1-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="07ae1-107">本逐步解說將說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="07ae1-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="07ae1-108">建立 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="07ae1-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="07ae1-109">建立表單的主功能表。</span><span class="sxs-lookup"><span data-stu-id="07ae1-109">Creating the main menu for your form.</span></span> <span data-ttu-id="07ae1-110">功能表的實際名稱會有所不同。</span><span class="sxs-lookup"><span data-stu-id="07ae1-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="07ae1-111">將 <xref:System.Windows.Forms.ToolStripPanel> 控制項加入至 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="07ae1-112">建立子表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-112">Creating a child form.</span></span>

- <span data-ttu-id="07ae1-113">依迭置順序排列 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="07ae1-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="07ae1-114">當您完成時，您將會有一個支援功能表合併和可移動 <xref:System.Windows.Forms.ToolStrip> 控制項的 MDI 表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="07ae1-115">若要將本主題中的程式碼複製成單一清單，請參閱[如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="07ae1-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07ae1-116">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="07ae1-116">Prerequisites</span></span>

<span data-ttu-id="07ae1-117">您將需要 Visual Studio 才能完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="07ae1-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="07ae1-118">建立專案</span><span class="sxs-lookup"><span data-stu-id="07ae1-118">Create the project</span></span>

1. <span data-ttu-id="07ae1-119">在 Visual Studio 中，建立稱為**system.windows.forms.toolstrip.mdiform**的 Windows 應用程式專案（**檔案 > \*\* **新增** > **專案** > **Visual C#** 或**Visual Basic\*\* > **傳統桌面** > **Windows Forms 應用程式**）。</span><span class="sxs-lookup"><span data-stu-id="07ae1-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="07ae1-120">在 Windows Form 設計工具中，選取表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="07ae1-121">在 屬性視窗中，將 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 的值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="07ae1-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="07ae1-122">建立主功能表</span><span class="sxs-lookup"><span data-stu-id="07ae1-122">Create the main menu</span></span>

<span data-ttu-id="07ae1-123">父 MDI 表單包含主功能表。</span><span class="sxs-lookup"><span data-stu-id="07ae1-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="07ae1-124">主功能表有一個名為**Window**的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="07ae1-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="07ae1-125">您可以使用 [**視窗]** 功能表項目來建立子表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="07ae1-126">子表單中的功能表項目會合並到主功能表中。</span><span class="sxs-lookup"><span data-stu-id="07ae1-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="07ae1-127">將 [<xref:System.Windows.Forms.MenuStrip>] 控制項從 [**工具箱**] 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="07ae1-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="07ae1-128">將 <xref:System.Windows.Forms.ToolStripMenuItem> 新增至 [<xref:System.Windows.Forms.MenuStrip>] 控制項，並將其命名為**視窗**。</span><span class="sxs-lookup"><span data-stu-id="07ae1-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="07ae1-129">選取 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="07ae1-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="07ae1-130">在 屬性視窗中，將 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性的值設定為 `ToolStripMenuItem1`。</span><span class="sxs-lookup"><span data-stu-id="07ae1-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="07ae1-131">將子專案新增至 [**視窗]** 功能表項目，然後將 [子專案] 命名為**New**。</span><span class="sxs-lookup"><span data-stu-id="07ae1-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="07ae1-132">在 屬性視窗中，按一下 **事件**。</span><span class="sxs-lookup"><span data-stu-id="07ae1-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="07ae1-133">按兩下 [<xref:System.Windows.Forms.ToolStripItem.Click>] 事件。</span><span class="sxs-lookup"><span data-stu-id="07ae1-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="07ae1-134">Windows Form 設計工具會產生 <xref:System.Windows.Forms.ToolStripItem.Click> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="07ae1-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="07ae1-135">將下列程式碼插入事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="07ae1-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="07ae1-136">將 ToolStripPanel 控制項新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="07ae1-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="07ae1-137">當您使用具有 MDI 表單的 <xref:System.Windows.Forms.MenuStrip> 控制項時，必須擁有 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="07ae1-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="07ae1-138">您必須將 <xref:System.Windows.Forms.ToolStripPanel> 控制項加入 [**工具箱**] 中，才能在 Windows Form 設計工具中建立 MDI 表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="07ae1-139">開啟 [**工具箱**]，然後按一下 [**所有 Windows Forms** ] 索引標籤，以顯示可用的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="07ae1-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="07ae1-140">以滑鼠右鍵按一下以開啟快捷方式功能表，然後選取 **[選擇專案**]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="07ae1-141">在 [**選擇工具箱專案**] 對話方塊中，在 [**名稱**] 欄中向下拖曳，直到您找到 [ **ToolStripPanel**]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="07ae1-142">選取**ToolStripPanel**的核取方塊，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="07ae1-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="07ae1-143">[<xref:System.Windows.Forms.ToolStripPanel>] 控制項會出現在 [**工具箱**] 中。</span><span class="sxs-lookup"><span data-stu-id="07ae1-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="07ae1-144">建立子表單</span><span class="sxs-lookup"><span data-stu-id="07ae1-144">Create a child form</span></span>

<span data-ttu-id="07ae1-145">在這個程式中，您將定義具有自己的 <xref:System.Windows.Forms.MenuStrip> 控制項的個別子表單類別。</span><span class="sxs-lookup"><span data-stu-id="07ae1-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="07ae1-146">這個表單的功能表項目會與父表單的專案合併。</span><span class="sxs-lookup"><span data-stu-id="07ae1-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="07ae1-147">將名為 `ChildForm` 的新表單新增至專案。</span><span class="sxs-lookup"><span data-stu-id="07ae1-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="07ae1-148">如需詳細資訊，請參閱[如何：將 Windows Forms 新增至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="07ae1-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="07ae1-149">將 [<xref:System.Windows.Forms.MenuStrip>] 控制項從 [**工具箱**] 拖曳至子表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="07ae1-150">按一下 <xref:System.Windows.Forms.MenuStrip> 控制項的設計工具動作圖像（![小型黑色箭號](./media/designer-actions-glyph.gif)），然後選取 [**編輯專案**]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-150">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="07ae1-151">在 [**專案集合編輯器**] 對話方塊中，將名為**ChildMenuItem**的新 <xref:System.Windows.Forms.ToolStripMenuItem> 新增至子功能表。</span><span class="sxs-lookup"><span data-stu-id="07ae1-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="07ae1-152">如需詳細資訊，請參閱[ToolStrip 專案集合編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="07ae1-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="07ae1-153">測試表單</span><span class="sxs-lookup"><span data-stu-id="07ae1-153">Test the form</span></span>

1. <span data-ttu-id="07ae1-154">按**F5**以編譯並執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="07ae1-155">按一下 [**視窗]** 功能表項目以開啟功能表，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="07ae1-156">會在表單的 MDI 工作區中建立新的子表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="07ae1-157">子表單的功能表會與主功能表合併。</span><span class="sxs-lookup"><span data-stu-id="07ae1-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="07ae1-158">關閉子表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-158">Close the child form.</span></span>

     <span data-ttu-id="07ae1-159">子表單的功能表會從主功能表中移除。</span><span class="sxs-lookup"><span data-stu-id="07ae1-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="07ae1-160">按一下 [**新增**數次]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-160">Click **New** several times.</span></span>

     <span data-ttu-id="07ae1-161">子表單會自動列在 [**視窗]** 功能表項目底下，因為已指派 <xref:System.Windows.Forms.MenuStrip> 控制項的 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="07ae1-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="07ae1-162">新增 ToolStrip 支援</span><span class="sxs-lookup"><span data-stu-id="07ae1-162">Add ToolStrip support</span></span>

<span data-ttu-id="07ae1-163">在這個程式中，您會將四個 <xref:System.Windows.Forms.ToolStrip> 控制項加入至 MDI 父表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="07ae1-164">每個 <xref:System.Windows.Forms.ToolStrip> 控制項都會加入 <xref:System.Windows.Forms.ToolStripPanel> 控制項內，並停駐在表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="07ae1-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="07ae1-165">將 [<xref:System.Windows.Forms.ToolStripPanel>] 控制項從 [**工具箱**] 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="07ae1-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="07ae1-166">選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項，然後按兩下 [**工具箱**] 中的 [<xref:System.Windows.Forms.ToolStrip>] 控制項。</span><span class="sxs-lookup"><span data-stu-id="07ae1-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="07ae1-167"><xref:System.Windows.Forms.ToolStrip> 控制項會在 <xref:System.Windows.Forms.ToolStripPanel> 控制項中建立。</span><span class="sxs-lookup"><span data-stu-id="07ae1-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="07ae1-168">選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="07ae1-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="07ae1-169">在 屬性視窗中，將控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值變更為 <xref:System.Windows.Forms.DockStyle.Left>。</span><span class="sxs-lookup"><span data-stu-id="07ae1-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="07ae1-170"><xref:System.Windows.Forms.ToolStripPanel> 控制項會停駐在主功能表下方的表單左邊。</span><span class="sxs-lookup"><span data-stu-id="07ae1-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="07ae1-171">MDI 工作區會調整大小以符合 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="07ae1-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="07ae1-172">重複步驟1到4。</span><span class="sxs-lookup"><span data-stu-id="07ae1-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="07ae1-173">將新的 <xref:System.Windows.Forms.ToolStripPanel> 控制項停駐在表單頂端。</span><span class="sxs-lookup"><span data-stu-id="07ae1-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="07ae1-174"><xref:System.Windows.Forms.ToolStripPanel> 控制項停駐在主功能表底下，但位於第一個 <xref:System.Windows.Forms.ToolStripPanel> 控制項的右邊。</span><span class="sxs-lookup"><span data-stu-id="07ae1-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="07ae1-175">此步驟說明在正確定位 <xref:System.Windows.Forms.ToolStripPanel> 控制項時，迭置順序的重要性。</span><span class="sxs-lookup"><span data-stu-id="07ae1-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="07ae1-176">針對兩個 <xref:System.Windows.Forms.ToolStripPanel> 控制項重複步驟1到4。</span><span class="sxs-lookup"><span data-stu-id="07ae1-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="07ae1-177">將新的 <xref:System.Windows.Forms.ToolStripPanel> 控制項停駐在表單的右邊和底部。</span><span class="sxs-lookup"><span data-stu-id="07ae1-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="07ae1-178">依迭置順序排列 ToolStripPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="07ae1-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="07ae1-179">停駐的 <xref:System.Windows.Forms.ToolStripPanel> 控制項在 MDI 表單上的位置是由控制項在迭置順序中的位置決定。</span><span class="sxs-lookup"><span data-stu-id="07ae1-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="07ae1-180">您可以輕鬆地在 [檔大綱] 視窗中排列控制項的迭置順序。</span><span class="sxs-lookup"><span data-stu-id="07ae1-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="07ae1-181">在 [ **View** ] 功能表中，按一下 [**其他視窗**]，然後按一下 [**檔大綱**]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="07ae1-182">上一個程式中 <xref:System.Windows.Forms.ToolStripPanel> 控制項的相片順序並不是標準的。</span><span class="sxs-lookup"><span data-stu-id="07ae1-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="07ae1-183">這是因為迭置順序不正確。</span><span class="sxs-lookup"><span data-stu-id="07ae1-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="07ae1-184">使用 [檔大綱] 視窗，即可變更控制項的迭置順序。</span><span class="sxs-lookup"><span data-stu-id="07ae1-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="07ae1-185">在 [檔大綱] 視窗中，選取 [ **ToolStripPanel4**]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="07ae1-186">重複按一下向下箭號按鈕，直到**ToolStripPanel4**位於清單的底部。</span><span class="sxs-lookup"><span data-stu-id="07ae1-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="07ae1-187">**ToolStripPanel4**控制項會停駐在表單底部的其他控制項底下。</span><span class="sxs-lookup"><span data-stu-id="07ae1-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="07ae1-188">選取 [ **ToolStripPanel2**]。</span><span class="sxs-lookup"><span data-stu-id="07ae1-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="07ae1-189">按一下向下箭號按鈕一次，將控制項第三個位置放在清單中。</span><span class="sxs-lookup"><span data-stu-id="07ae1-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="07ae1-190">**ToolStripPanel2**控制項會停駐在表單的頂端，並放在主功能表下方和其他控制項的上方。</span><span class="sxs-lookup"><span data-stu-id="07ae1-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="07ae1-191">在 [**檔大綱**] 視窗中選取各種控制項，然後將它們移至迭置順序中的不同位置。</span><span class="sxs-lookup"><span data-stu-id="07ae1-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="07ae1-192">請注意，停駐控制項的位置上，迭置順序的效果。</span><span class="sxs-lookup"><span data-stu-id="07ae1-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="07ae1-193">使用 CTRL-Z 或 [**編輯**] 功能表上的 [**復原**] 來復原變更。</span><span class="sxs-lookup"><span data-stu-id="07ae1-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="07ae1-194">檢查點-測試您的表單</span><span class="sxs-lookup"><span data-stu-id="07ae1-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="07ae1-195">按**F5**以編譯並執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="07ae1-196">按一下 <xref:System.Windows.Forms.ToolStrip> 控制項的底框，並將控制項拖曳至表單上的不同位置。</span><span class="sxs-lookup"><span data-stu-id="07ae1-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="07ae1-197">您可以將 <xref:System.Windows.Forms.ToolStrip> 控制項從一個 <xref:System.Windows.Forms.ToolStripPanel> 控制項拖曳至另一個。</span><span class="sxs-lookup"><span data-stu-id="07ae1-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="07ae1-198">後續步驟</span><span class="sxs-lookup"><span data-stu-id="07ae1-198">Next steps</span></span>

<span data-ttu-id="07ae1-199">在本逐步解說中，您已建立具有 <xref:System.Windows.Forms.ToolStrip> 控制項和功能表合併的 MDI 父表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="07ae1-200">您可以將 <xref:System.Windows.Forms.ToolStrip> 系列控制項用於其他許多用途：</span><span class="sxs-lookup"><span data-stu-id="07ae1-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="07ae1-201">使用 <xref:System.Windows.Forms.ContextMenuStrip>建立控制項的快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="07ae1-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="07ae1-202">如需詳細資訊，請參閱[CoNtextMenu 元件總覽](contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="07ae1-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="07ae1-203">建立具有自動填入標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="07ae1-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="07ae1-204">如需詳細資訊，請參閱[逐步解說：提供標準功能表項目給表單](walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="07ae1-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="07ae1-205">為您的 <xref:System.Windows.Forms.ToolStrip> 控制項提供專業的外觀。</span><span class="sxs-lookup"><span data-stu-id="07ae1-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="07ae1-206">如需詳細資訊，請參閱[如何：設定應用程式的 ToolStrip](how-to-set-the-toolstrip-renderer-for-an-application.md)轉譯器。</span><span class="sxs-lookup"><span data-stu-id="07ae1-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07ae1-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07ae1-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="07ae1-208">操作說明：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="07ae1-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="07ae1-209">操作說明：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="07ae1-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="07ae1-210">操作說明：將 MenuStrip 插入至 MDI 下拉式功能表</span><span class="sxs-lookup"><span data-stu-id="07ae1-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="07ae1-211">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="07ae1-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
