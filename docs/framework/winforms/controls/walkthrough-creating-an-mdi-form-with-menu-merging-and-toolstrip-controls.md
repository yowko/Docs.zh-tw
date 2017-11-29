---
title: "逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單"
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
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bca5439f247951496d82c03b57ec1fa0e21a8271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="2295c-102">逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單</span><span class="sxs-lookup"><span data-stu-id="2295c-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="2295c-103"><xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。</span><span class="sxs-lookup"><span data-stu-id="2295c-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="2295c-104">MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。</span><span class="sxs-lookup"><span data-stu-id="2295c-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="2295c-105">本逐步解說示範如何使用<xref:System.Windows.Forms.ToolStripPanel>在 MDI 表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="2295c-106">這個表單也支援子功能表的功能表合併。</span><span class="sxs-lookup"><span data-stu-id="2295c-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="2295c-107">在本逐步解說說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="2295c-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="2295c-108">建立 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="2295c-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="2295c-109">建立主功能表為您的表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-109">Creating the main menu for your form.</span></span> <span data-ttu-id="2295c-110">[] 功能表中的實際名稱而異。</span><span class="sxs-lookup"><span data-stu-id="2295c-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="2295c-111">加入<xref:System.Windows.Forms.ToolStripPanel>控制權傳輸至**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="2295c-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="2295c-112">建立子表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="2295c-113">排列<xref:System.Windows.Forms.ToolStripPanel>依 z 軸順序的控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="2295c-114">當您完成時，您必須支援功能表合併和可移動的 MDI 表單<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="2295c-115">若要為單一列出本主題中複製的程式碼，請參閱[How to： 使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="2295c-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2295c-116">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="2295c-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2295c-117">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="2295c-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2295c-118">如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。</span><span class="sxs-lookup"><span data-stu-id="2295c-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2295c-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="2295c-119">Prerequisites</span></span>  
 <span data-ttu-id="2295c-120">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="2295c-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="2295c-121">若要能夠建立和執行 Windows Form 應用程式專案的電腦上有足夠的權限所在[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="2295c-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2295c-122">建立專案</span><span class="sxs-lookup"><span data-stu-id="2295c-122">Creating the Project</span></span>  
 <span data-ttu-id="2295c-123">第一個步驟是建立專案並設定表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="2295c-124">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="2295c-124">To create the project</span></span>  
  
1.  <span data-ttu-id="2295c-125">建立 Windows 應用程式專案，稱為**MdiForm**。</span><span class="sxs-lookup"><span data-stu-id="2295c-125">Create a Windows Application project called **MdiForm**.</span></span>  
  
     <span data-ttu-id="2295c-126">如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="2295c-126">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="2295c-127">在 Windows Form 設計工具中，選取的表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-127">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="2295c-128">在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.Form.IsMdiContainer%2A>至`true`。</span><span class="sxs-lookup"><span data-stu-id="2295c-128">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="2295c-129">建立主功能表</span><span class="sxs-lookup"><span data-stu-id="2295c-129">Creating the Main Menu</span></span>  
 <span data-ttu-id="2295c-130">MDI 父表單包含主功能表。</span><span class="sxs-lookup"><span data-stu-id="2295c-130">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="2295c-131">主功能表中有一個功能表項目名稱為**視窗**。</span><span class="sxs-lookup"><span data-stu-id="2295c-131">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="2295c-132">與**視窗**功能表項目，您可以建立子表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-132">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="2295c-133">從子表單的功能表項目會合併到主功能表。</span><span class="sxs-lookup"><span data-stu-id="2295c-133">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="2295c-134">若要建立主功能表</span><span class="sxs-lookup"><span data-stu-id="2295c-134">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="2295c-135">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="2295c-136">新增<xref:System.Windows.Forms.ToolStripMenuItem>至<xref:System.Windows.Forms.MenuStrip>控制項並將其命名**視窗**。</span><span class="sxs-lookup"><span data-stu-id="2295c-136">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="2295c-137">選取 <xref:System.Windows.Forms.MenuStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-137">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="2295c-138">在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性`ToolStripMenuItem1`。</span><span class="sxs-lookup"><span data-stu-id="2295c-138">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="2295c-139">加入至一個子項目**視窗**功能表項目，然後名稱子項目的**新增**。</span><span class="sxs-lookup"><span data-stu-id="2295c-139">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="2295c-140">在 [屬性] 視窗中，按一下**事件**。</span><span class="sxs-lookup"><span data-stu-id="2295c-140">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="2295c-141">按兩下<xref:System.Windows.Forms.ToolStripItem.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="2295c-141">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="2295c-142">Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="2295c-142">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="2295c-143">此事件處理常式中插入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="2295c-143">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="2295c-144">ToolStripPanel 控制項新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="2295c-144">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="2295c-145">當您使用<xref:System.Windows.Forms.MenuStrip>控制項，您必須擁有在 MDI 表單<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-145">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="2295c-146">您必須新增<xref:System.Windows.Forms.ToolStripPanel>控制權傳輸至**工具箱**來建置您在 Windows Form 設計工具中的 MDI 表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-146">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="2295c-147">ToolStripPanel 控制項加入 [工具箱]</span><span class="sxs-lookup"><span data-stu-id="2295c-147">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="2295c-148">開啟**工具箱**，然後按一下 **所有 Windows Form**索引標籤，以顯示可用的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-148">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="2295c-149">若要開啟快顯功能表中，以滑鼠右鍵按一下並選取**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="2295c-149">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="2295c-150">在**選擇工具箱項目**對話方塊中，向下捲動**名稱**資料行，直到您找到**ToolStripPanel**。</span><span class="sxs-lookup"><span data-stu-id="2295c-150">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="2295c-151">選取核取方塊，由**ToolStripPanel**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="2295c-151">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="2295c-152"><xref:System.Windows.Forms.ToolStripPanel>控制項出現在**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="2295c-152">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="2295c-153">建立子表單</span><span class="sxs-lookup"><span data-stu-id="2295c-153">Creating a Child Form</span></span>  
 <span data-ttu-id="2295c-154">在此程序，您會定義不同的子表單類別，都有它自己<xref:System.Windows.Forms.MenuStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-154">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="2295c-155">此表單的功能表項目會與父表單的合併。</span><span class="sxs-lookup"><span data-stu-id="2295c-155">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="2295c-156">若要定義子表單</span><span class="sxs-lookup"><span data-stu-id="2295c-156">To define a child form</span></span>  
  
1.  <span data-ttu-id="2295c-157">加入名為的新表單`ChildForm`至專案。</span><span class="sxs-lookup"><span data-stu-id="2295c-157">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="2295c-158">如需詳細資訊，請參閱[How to： 將 Windows Form 加入至專案](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)。</span><span class="sxs-lookup"><span data-stu-id="2295c-158">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="2295c-159">從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至子表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-159">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="2295c-160">按一下<xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**編輯項目**。</span><span class="sxs-lookup"><span data-stu-id="2295c-160">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="2295c-161">在**項目集合編輯器**對話方塊方塊中，加入新<xref:System.Windows.Forms.ToolStripMenuItem>名為**ChildMenuItem**子功能表。</span><span class="sxs-lookup"><span data-stu-id="2295c-161">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="2295c-162">如需詳細資訊，請參閱[ToolStrip 項目集合編輯器](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25)。</span><span class="sxs-lookup"><span data-stu-id="2295c-162">For more information, see [ToolStrip Items Collection Editor](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="2295c-163">測試表單</span><span class="sxs-lookup"><span data-stu-id="2295c-163">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="2295c-164">若要測試您的表單</span><span class="sxs-lookup"><span data-stu-id="2295c-164">To test your form</span></span>  
  
1.  <span data-ttu-id="2295c-165">按 F5 編譯和執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-165">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="2295c-166">按一下**視窗**功能表項目，以開啟功能表，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="2295c-166">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="2295c-167">表單的 MDI 工作區中建立新的子表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-167">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="2295c-168">子表單的功能表和功能表合併主功能表。</span><span class="sxs-lookup"><span data-stu-id="2295c-168">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="2295c-169">關閉子表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-169">Close the child form.</span></span>  
  
     <span data-ttu-id="2295c-170">子表單的功能表會從主功能表中移除。</span><span class="sxs-lookup"><span data-stu-id="2295c-170">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="2295c-171">按一下**新增**數次。</span><span class="sxs-lookup"><span data-stu-id="2295c-171">Click **New** several times.</span></span>  
  
     <span data-ttu-id="2295c-172">子表單自動列在 W**視窗**功能表項目，因為<xref:System.Windows.Forms.MenuStrip>控制項的<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性指派。</span><span class="sxs-lookup"><span data-stu-id="2295c-172">The child forms are automatically listed under the W**indow** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="2295c-173">加入 ToolStrip 支援</span><span class="sxs-lookup"><span data-stu-id="2295c-173">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="2295c-174">在此程序，您會將四個<xref:System.Windows.Forms.ToolStrip>MDI 父表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-174">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="2295c-175">每個<xref:System.Windows.Forms.ToolStrip>內加入控制項<xref:System.Windows.Forms.ToolStripPanel>控制項停駐在表單的邊緣。</span><span class="sxs-lookup"><span data-stu-id="2295c-175">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="2295c-176">MDI 父表單中加入 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="2295c-176">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="2295c-177">從**工具箱**，拖曳<xref:System.Windows.Forms.ToolStripPanel>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-177">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="2295c-178">與<xref:System.Windows.Forms.ToolStripPanel>選取控制項中，按兩下<xref:System.Windows.Forms.ToolStrip>控制**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="2295c-178">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="2295c-179">A<xref:System.Windows.Forms.ToolStrip>中建立控制項<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-179">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="2295c-180">選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-180">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="2295c-181">在 [屬性] 視窗中，變更控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Left>。</span><span class="sxs-lookup"><span data-stu-id="2295c-181">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="2295c-182"><xref:System.Windows.Forms.ToolStripPanel>控制停駐在主功能表下的表單的左邊。</span><span class="sxs-lookup"><span data-stu-id="2295c-182">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="2295c-183">在 MDI 工作區調整大小以配合<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-183">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="2295c-184">重複步驟 1 到 4。</span><span class="sxs-lookup"><span data-stu-id="2295c-184">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="2295c-185">新的停駐<xref:System.Windows.Forms.ToolStripPanel>表單頂端的控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-185">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="2295c-186"><xref:System.Windows.Forms.ToolStripPanel>控制項下方主功能表中，但右邊的第一個停駐<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-186">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="2295c-187">此步驟中說明在正確位置中的疊置順序的重要性<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-187">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="2295c-188">重複步驟 1 到 4 的另外兩個<xref:System.Windows.Forms.ToolStripPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-188">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="2295c-189">新的停駐<xref:System.Windows.Forms.ToolStripPanel>的權限和表單底部的控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-189">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="2295c-190">排列依 z 軸順序 ToolStripPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="2295c-190">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="2295c-191">停駐的位置<xref:System.Windows.Forms.ToolStripPanel>MDI 表單上的控制項由控制項的疊置順序的位置。</span><span class="sxs-lookup"><span data-stu-id="2295c-191">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="2295c-192">您可以輕易地排列您在文件大綱 視窗中的控制項疊置順序。</span><span class="sxs-lookup"><span data-stu-id="2295c-192">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="2295c-193">若要排列依 z 軸順序 ToolStripPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="2295c-193">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="2295c-194">在**檢視**功能表上，按一下 **其他視窗**，然後按一下 **文件大綱**。</span><span class="sxs-lookup"><span data-stu-id="2295c-194">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="2295c-195">排列方式您<xref:System.Windows.Forms.ToolStripPanel>控制項，從上一個程序並非標準用法。</span><span class="sxs-lookup"><span data-stu-id="2295c-195">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="2295c-196">這是因為疊置順序不正確。</span><span class="sxs-lookup"><span data-stu-id="2295c-196">This is because the z-order is not correct.</span></span> <span data-ttu-id="2295c-197">您可以使用 [文件大綱] 視窗來變更控制項疊置順序。</span><span class="sxs-lookup"><span data-stu-id="2295c-197">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="2295c-198">在 [文件大綱] 視窗中，選取**ToolStripPanel4**。</span><span class="sxs-lookup"><span data-stu-id="2295c-198">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="2295c-199">按一下向下箭頭按鈕重複，直到**ToolStripPanel4**位於清單的底部。</span><span class="sxs-lookup"><span data-stu-id="2295c-199">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="2295c-200">**ToolStripPanel4**控制項停駐於底部下其他控制項的表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-200">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="2295c-201">選取**ToolStripPanel2**。</span><span class="sxs-lookup"><span data-stu-id="2295c-201">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="2295c-202">按一下一次向下箭號按鈕在清單中的第三個放置控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-202">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="2295c-203">**ToolStripPanel2**控制項停駐在表單下方主功能表和其他控制項上方的頂端。</span><span class="sxs-lookup"><span data-stu-id="2295c-203">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="2295c-204">選取不同的控制項中**文件大綱**視窗，並將它們移到疊置順序的不同位置。</span><span class="sxs-lookup"><span data-stu-id="2295c-204">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="2295c-205">請注意對於停駐控制項的位置之疊置順序的影響。</span><span class="sxs-lookup"><span data-stu-id="2295c-205">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="2295c-206">使用 CTRL-Z 或**復原**上**編輯**功能表來復原您的變更。</span><span class="sxs-lookup"><span data-stu-id="2295c-206">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="2295c-207">檢查點</span><span class="sxs-lookup"><span data-stu-id="2295c-207">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="2295c-208">若要測試您的表單</span><span class="sxs-lookup"><span data-stu-id="2295c-208">To test your form</span></span>  
  
1.  <span data-ttu-id="2295c-209">按 F5 編譯和執行您的表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-209">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="2295c-210">按一下的底框<xref:System.Windows.Forms.ToolStrip>控制，並在表單上將控制項拖曳到不同的位置。</span><span class="sxs-lookup"><span data-stu-id="2295c-210">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="2295c-211">您可以拖曳<xref:System.Windows.Forms.ToolStrip>控制項從某個<xref:System.Windows.Forms.ToolStripPanel>到另一個控制項。</span><span class="sxs-lookup"><span data-stu-id="2295c-211">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2295c-212">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2295c-212">Next Steps</span></span>  
 <span data-ttu-id="2295c-213">在本逐步解說，您已經建立 MDI 父表單與<xref:System.Windows.Forms.ToolStrip>控制項和功能表合併。</span><span class="sxs-lookup"><span data-stu-id="2295c-213">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="2295c-214">您可以使用<xref:System.Windows.Forms.ToolStrip>系列用於許多其他用途的控制項：</span><span class="sxs-lookup"><span data-stu-id="2295c-214">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="2295c-215">建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="2295c-215">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="2295c-216">如需詳細資訊，請參閱[ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="2295c-216">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="2295c-217">使用自動填入的標準功能表中建立的表單。</span><span class="sxs-lookup"><span data-stu-id="2295c-217">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="2295c-218">如需詳細資訊，請參閱[逐步解說： 提供標準功能表項目表單](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="2295c-218">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="2295c-219">提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。</span><span class="sxs-lookup"><span data-stu-id="2295c-219">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="2295c-220">如需詳細資訊，請參閱[How to： 設定應用程式的 ToolStrip 產生器](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="2295c-220">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2295c-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2295c-221">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="2295c-222">操作說明：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="2295c-222">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="2295c-223">操作說明：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="2295c-223">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="2295c-224">操作說明：將 MenuStrip 插入至 MDI 下拉式功能表</span><span class="sxs-lookup"><span data-stu-id="2295c-224">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="2295c-225">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="2295c-225">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
