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
ms.openlocfilehash: 49d9b10d8a87af1c3600756efe8dba3f81df90a6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717133"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="b59f2-102">逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單</span><span class="sxs-lookup"><span data-stu-id="b59f2-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="b59f2-103">
  <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。</span><span class="sxs-lookup"><span data-stu-id="b59f2-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="b59f2-104">MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。</span><span class="sxs-lookup"><span data-stu-id="b59f2-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="b59f2-105">本逐步解說示範如何使用<xref:System.Windows.Forms.ToolStripPanel>控制項搭配 MDI 表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="b59f2-106">這個表單也支援子功能表的功能表合併。</span><span class="sxs-lookup"><span data-stu-id="b59f2-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="b59f2-107">本逐步解說會說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="b59f2-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="b59f2-108">建立 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="b59f2-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="b59f2-109">建立主功能表為您的表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-109">Creating the main menu for your form.</span></span> <span data-ttu-id="b59f2-110">[] 功能表中的實際名稱而有所不同。</span><span class="sxs-lookup"><span data-stu-id="b59f2-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="b59f2-111">新增<xref:System.Windows.Forms.ToolStripPanel>若要控制**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="b59f2-112">建立子表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="b59f2-113">排列<xref:System.Windows.Forms.ToolStripPanel>依 z 軸順序的控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="b59f2-114">當您完成時，您必須支援功能表合併和可移動的 MDI 表單<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="b59f2-115">若要將此主題中的程式碼複製為單一清單，請參閱[如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="b59f2-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b59f2-116">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b59f2-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b59f2-117">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="b59f2-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b59f2-118">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="b59f2-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b59f2-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="b59f2-119">Prerequisites</span></span>  
 <span data-ttu-id="b59f2-120">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="b59f2-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="b59f2-121">若要能夠建立和安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="b59f2-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b59f2-122">建立專案</span><span class="sxs-lookup"><span data-stu-id="b59f2-122">Creating the Project</span></span>  
 <span data-ttu-id="b59f2-123">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="b59f2-124">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="b59f2-124">To create the project</span></span>  
  
1.  <span data-ttu-id="b59f2-125">建立 Windows 應用程式專案，稱為**MdiForm** (**檔案** > **新增** > **專案** > **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**).</span><span class="sxs-lookup"><span data-stu-id="b59f2-125">Create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="b59f2-126">在 Windows Form 設計工具中，選取的表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-126">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="b59f2-127">在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.Form.IsMdiContainer%2A>至`true`。</span><span class="sxs-lookup"><span data-stu-id="b59f2-127">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="b59f2-128">建立主功能表</span><span class="sxs-lookup"><span data-stu-id="b59f2-128">Creating the Main Menu</span></span>  
 <span data-ttu-id="b59f2-129">MDI 父表單包含主功能表。</span><span class="sxs-lookup"><span data-stu-id="b59f2-129">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="b59f2-130">主功能表中有一個功能表項目名為**視窗**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-130">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="b59f2-131">具有**視窗**功能表項目，您可以建立子表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-131">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="b59f2-132">從 子表單的功能表項目會合併到主功能表中。</span><span class="sxs-lookup"><span data-stu-id="b59f2-132">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="b59f2-133">若要建立主功能表</span><span class="sxs-lookup"><span data-stu-id="b59f2-133">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="b59f2-134">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="b59f2-135">新增<xref:System.Windows.Forms.ToolStripMenuItem>要<xref:System.Windows.Forms.MenuStrip>控制項並將它命名**視窗**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-135">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="b59f2-136">選取 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-136">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="b59f2-137">在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性設`ToolStripMenuItem1`。</span><span class="sxs-lookup"><span data-stu-id="b59f2-137">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="b59f2-138">新增至子項目的\*\* 視窗**功能表項目，然後命名子項目的**新增\*\*。</span><span class="sxs-lookup"><span data-stu-id="b59f2-138">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="b59f2-139">在 [屬性] 視窗中，按一下**事件**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-139">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="b59f2-140">按兩下<xref:System.Windows.Forms.ToolStripItem.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="b59f2-140">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="b59f2-141">Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="b59f2-141">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="b59f2-142">事件處理常式中插入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b59f2-142">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="b59f2-143">ToolStripPanel 控制項新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="b59f2-143">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="b59f2-144">當您使用<xref:System.Windows.Forms.MenuStrip>控制項，您必須擁有在 MDI 表單<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-144">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="b59f2-145">您必須新增<xref:System.Windows.Forms.ToolStripPanel>若要控制**工具箱**來建置您在 Windows Form 設計工具中的 MDI 表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-145">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="b59f2-146">ToolStripPanel 控制項新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="b59f2-146">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="b59f2-147">開啟**工具箱**，然後按一下**所有的 Windows Form**索引標籤，以顯示可用的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-147">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="b59f2-148">以滑鼠右鍵按一下以開啟捷徑功能表，然後選取**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-148">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="b59f2-149">在 [**選擇工具箱項目**] 對話方塊中，向下捲動**名稱**資料行，直到您找到**ToolStripPanel**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-149">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="b59f2-150">選取核取方塊**ToolStripPanel**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-150">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b59f2-151"><xref:System.Windows.Forms.ToolStripPanel>控制項會出現在**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-151">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="b59f2-152">建立子表單</span><span class="sxs-lookup"><span data-stu-id="b59f2-152">Creating a Child Form</span></span>  
 <span data-ttu-id="b59f2-153">在此程序中，您將定義個別的子表單類別，都有它自己<xref:System.Windows.Forms.MenuStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-153">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="b59f2-154">這種形式的功能表項目會與父表單的合併。</span><span class="sxs-lookup"><span data-stu-id="b59f2-154">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="b59f2-155">若要定義子表單</span><span class="sxs-lookup"><span data-stu-id="b59f2-155">To define a child form</span></span>  
  
1.  <span data-ttu-id="b59f2-156">加入新的表單名為`ChildForm`至專案。</span><span class="sxs-lookup"><span data-stu-id="b59f2-156">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="b59f2-157">如需詳細資訊，請參閱[如何：將 Windows Form 加入專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="b59f2-157">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="b59f2-158">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>拖曳至子表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-158">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="b59f2-159">按一下 <xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 （glyph) (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**編輯項目**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-159">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="b59f2-160">在 **項目集合編輯器**對話方塊方塊中，加入新<xref:System.Windows.Forms.ToolStripMenuItem>名為**ChildMenuItem**子功能表。</span><span class="sxs-lookup"><span data-stu-id="b59f2-160">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="b59f2-161">如需詳細資訊，請參閱 < [ToolStrip 項目集合編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="b59f2-161">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="b59f2-162">測試表單</span><span class="sxs-lookup"><span data-stu-id="b59f2-162">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="b59f2-163">若要測試您的表單</span><span class="sxs-lookup"><span data-stu-id="b59f2-163">To test your form</span></span>  
  
1.  <span data-ttu-id="b59f2-164">按 F5 以編譯並執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-164">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="b59f2-165">按一下 [ **] 視窗**以開啟功能表，然後按一下功能表項目**新增**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-165">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="b59f2-166">表單的 MDI 工作區中建立新的子表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-166">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="b59f2-167">在主功能表會合併子表單的功能表。</span><span class="sxs-lookup"><span data-stu-id="b59f2-167">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="b59f2-168">關閉子表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-168">Close the child form.</span></span>  
  
     <span data-ttu-id="b59f2-169">從主功能表中，移除子表單的功能表。</span><span class="sxs-lookup"><span data-stu-id="b59f2-169">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="b59f2-170">按一下 **新增**數次。</span><span class="sxs-lookup"><span data-stu-id="b59f2-170">Click **New** several times.</span></span>  
  
     <span data-ttu-id="b59f2-171">子表單並自動列底下\*\* 視窗\*\*功能表項目，因為<xref:System.Windows.Forms.MenuStrip>控制項的<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性指派。</span><span class="sxs-lookup"><span data-stu-id="b59f2-171">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="b59f2-172">新增 ToolStrip 支援</span><span class="sxs-lookup"><span data-stu-id="b59f2-172">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="b59f2-173">在此程序中，您會將四個<xref:System.Windows.Forms.ToolStrip>MDI 父表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-173">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="b59f2-174">每個<xref:System.Windows.Forms.ToolStrip>控制項會加入內<xref:System.Windows.Forms.ToolStripPanel>控制項停駐在表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="b59f2-174">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="b59f2-175">若要加入的 MDI 父表單中的 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="b59f2-175">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="b59f2-176">從**工具箱**，拖曳<xref:System.Windows.Forms.ToolStripPanel>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-176">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="b59f2-177">具有<xref:System.Windows.Forms.ToolStripPanel>選取控制項中，按兩下<xref:System.Windows.Forms.ToolStrip>控制中**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-177">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="b59f2-178">A<xref:System.Windows.Forms.ToolStrip>控制項建立<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-178">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="b59f2-179">選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-179">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="b59f2-180">在 [屬性] 視窗中，變更控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Left>。</span><span class="sxs-lookup"><span data-stu-id="b59f2-180">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="b59f2-181"><xref:System.Windows.Forms.ToolStripPanel>控制項停駐在主功能表下的表單的左邊。</span><span class="sxs-lookup"><span data-stu-id="b59f2-181">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="b59f2-182">在 MDI 工作區調整大小以配合<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-182">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="b59f2-183">重複步驟 1 到 4。</span><span class="sxs-lookup"><span data-stu-id="b59f2-183">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="b59f2-184">新的停駐<xref:System.Windows.Forms.ToolStripPanel>表單頂端的控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-184">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="b59f2-185"><xref:System.Windows.Forms.ToolStripPanel>主功能表下，但右邊的第一個控制項所停駐<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-185">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="b59f2-186">此步驟說明如何在正確位置中的疊置順序的重要性<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-186">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="b59f2-187">重複步驟 1 到 4 的另外兩個<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-187">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="b59f2-188">新的停駐<xref:System.Windows.Forms.ToolStripPanel>到右邊，並在表單底部的控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-188">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="b59f2-189">排列 ToolStripPanel 控制項的疊置順序</span><span class="sxs-lookup"><span data-stu-id="b59f2-189">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="b59f2-190">停駐的位置<xref:System.Windows.Forms.ToolStripPanel>MDI 表單上的控制項由控制項的疊置順序位置。</span><span class="sxs-lookup"><span data-stu-id="b59f2-190">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="b59f2-191">您可以輕易地排列控制項在文件大綱 視窗中的 z-order。</span><span class="sxs-lookup"><span data-stu-id="b59f2-191">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="b59f2-192">依 z 軸順序排列 ToolStripPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="b59f2-192">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="b59f2-193">在 **檢視** 功能表中，按一下**其他 Windows**，然後按一下 **文件大綱**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-193">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="b59f2-194">排列方式您<xref:System.Windows.Forms.ToolStripPanel>控制項從上一個程序並非標準用法。</span><span class="sxs-lookup"><span data-stu-id="b59f2-194">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="b59f2-195">這是因為疊置順序不正確。</span><span class="sxs-lookup"><span data-stu-id="b59f2-195">This is because the z-order is not correct.</span></span> <span data-ttu-id="b59f2-196">您可以使用 [文件大綱] 視窗來變更控制項疊置順序。</span><span class="sxs-lookup"><span data-stu-id="b59f2-196">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="b59f2-197">在 [文件大綱] 視窗中，選取**ToolStripPanel4**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-197">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="b59f2-198">按一下向下箭頭按鈕重複，直到**ToolStripPanel4**位於清單底部。</span><span class="sxs-lookup"><span data-stu-id="b59f2-198">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="b59f2-199">**ToolStripPanel4**控制項所停駐到其他控制項下的表單底部。</span><span class="sxs-lookup"><span data-stu-id="b59f2-199">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="b59f2-200">選取  **ToolStripPanel2**。</span><span class="sxs-lookup"><span data-stu-id="b59f2-200">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="b59f2-201">控制項第三個位置清單中按一下向下箭頭按鈕一次。</span><span class="sxs-lookup"><span data-stu-id="b59f2-201">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="b59f2-202">**ToolStripPanel2**控制項停駐在表單中，主功能表下方以及高於其他控制項的頂端。</span><span class="sxs-lookup"><span data-stu-id="b59f2-202">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="b59f2-203">選取不同的控制項中**文件大綱**視窗並將其移到疊置順序的不同位置。</span><span class="sxs-lookup"><span data-stu-id="b59f2-203">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="b59f2-204">請注意位置停駐控制項的疊置順序的影響。</span><span class="sxs-lookup"><span data-stu-id="b59f2-204">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="b59f2-205">使用 CTRL-Z 或**恢復**上**編輯**功能表來復原您的變更。</span><span class="sxs-lookup"><span data-stu-id="b59f2-205">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="b59f2-206">檢查點</span><span class="sxs-lookup"><span data-stu-id="b59f2-206">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="b59f2-207">若要測試您的表單</span><span class="sxs-lookup"><span data-stu-id="b59f2-207">To test your form</span></span>  
  
1.  <span data-ttu-id="b59f2-208">按 F5 以編譯並執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-208">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="b59f2-209">按 的底框<xref:System.Windows.Forms.ToolStrip>控制項，並在表單上，將控制項拖曳至不同的位置。</span><span class="sxs-lookup"><span data-stu-id="b59f2-209">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="b59f2-210">您可以拖曳<xref:System.Windows.Forms.ToolStrip>控制項從某個<xref:System.Windows.Forms.ToolStripPanel>到另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="b59f2-210">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b59f2-211">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b59f2-211">Next Steps</span></span>  
 <span data-ttu-id="b59f2-212">在本逐步解說中，您已建立 MDI 父表單與<xref:System.Windows.Forms.ToolStrip>控制項和功能表合併。</span><span class="sxs-lookup"><span data-stu-id="b59f2-212">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="b59f2-213">您可以使用<xref:System.Windows.Forms.ToolStrip>用於許多其他用途的控制項系列：</span><span class="sxs-lookup"><span data-stu-id="b59f2-213">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="b59f2-214">建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="b59f2-214">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="b59f2-215">如需詳細資訊，請參閱 < [ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b59f2-215">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="b59f2-216">使用自動填入的標準功能表中建立的表單。</span><span class="sxs-lookup"><span data-stu-id="b59f2-216">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="b59f2-217">如需詳細資訊，請參閱[逐步解說：對表單提供標準功能表項目](walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="b59f2-217">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="b59f2-218">提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。</span><span class="sxs-lookup"><span data-stu-id="b59f2-218">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="b59f2-219">如需詳細資訊，請參閱[如何：設定應用程式的 ToolStrip 產生器](how-to-set-the-toolstrip-renderer-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b59f2-219">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59f2-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b59f2-220">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="b59f2-221">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="b59f2-221">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="b59f2-222">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="b59f2-222">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="b59f2-223">如何：將 MenuStrip 插入至 MDI 下拉式功能表</span><span class="sxs-lookup"><span data-stu-id="b59f2-223">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="b59f2-224">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="b59f2-224">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
