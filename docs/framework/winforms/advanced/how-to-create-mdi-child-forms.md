---
title: HOW TO：建立 MDI 子表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 73f2004470d5d1da04199af75832cefd6348ce18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342454"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="1dbf6-102">HOW TO：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="1dbf6-102">How to: Create MDI Child Forms</span></span>
<span data-ttu-id="1dbf6-103">MDI 子表單是不可或缺的元素[多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)，如下列形式會使用者互動的中心。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>  
  
 <span data-ttu-id="1dbf6-104">在下列程序中，您將建立顯示 <xref:System.Windows.Forms.RichTextBox> 控制項的 MDI 子表單，這和大多數文書處理應用程式類似。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-104">In the following procedure, you will create MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="1dbf6-105">以其他控制項 (例如 <xref:System.Windows.Forms.DataGridView> 控制項) 或混合控制項來取代 <xref:System.Windows.Forms> 控制項，可讓您建立各種可能的 MDI 子視窗 (甚至是 MDI 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dbf6-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1dbf6-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1dbf6-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-mdi-child-forms"></a><span data-ttu-id="1dbf6-109">建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="1dbf6-109">To create MDI child forms</span></span>  
  
1. <span data-ttu-id="1dbf6-110">建立新的 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-110">Create a new Windows Forms project.</span></span> <span data-ttu-id="1dbf6-111">在**屬性 Windows**表單中，設定其<xref:System.Windows.Forms.Form.IsMdiContainer%2A>屬性設`true`，並將其`WindowsState`屬性設`Maximized`。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-111">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>  
  
     <span data-ttu-id="1dbf6-112">如此即可將表單指定為子視窗的 MDI 容器。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-112">This designates the form as an MDI container for child windows.</span></span>  
  
2. <span data-ttu-id="1dbf6-113">將 <xref:System.Windows.Forms.MenuStrip> 控制項從 [`Toolbox`] 拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-113">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="1dbf6-114">設定其`Text`屬性，以**檔案**。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-114">Set its `Text` property to **File**.</span></span>  
  
3. <span data-ttu-id="1dbf6-115">按一下旁邊的省略符號 （...）**項目**屬性，然後按一下**新增**加入兩個子工具區域功能表項目。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-115">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="1dbf6-116">設定`Text`屬性，這些項目的**新增**並**視窗**。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-116">Set the `Text` property for these items to **New** and **Window**.</span></span>  
  
4. <span data-ttu-id="1dbf6-117">在 [**方案總管] 中**，以滑鼠右鍵按一下專案，指向**新增**，然後選取**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-117">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>  
  
5. <span data-ttu-id="1dbf6-118">在 **加入新項目**對話方塊方塊中，選取**Windows 表單**（在 Visual Basic 或 Visual C# 中） 或**Windows Forms 應用程式 (.NET)** (在[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 從**範本**窗格。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-118">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="1dbf6-119">在 **名稱**方塊中，將表單命名**Form2**。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-119">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="1dbf6-120">按一下 **開啟**按鈕以新增至專案的表單。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-120">Click the **Open** button to add the form to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1dbf6-121">您在這個步驟中所建立的 MDI 子表單是標準的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-121">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="1dbf6-122">因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性，可讓您控制表單的透明度。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-122">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="1dbf6-123">然而，<xref:System.Windows.Forms.Form.Opacity%2A> 屬性是專為最上層視窗而設計的。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-123">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="1dbf6-124">請勿搭配 MDI 子表單使用這個屬性，這樣做可能會發生繪製問題。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-124">Do not use it with MDI child forms, as painting problems can occur.</span></span>  
  
     <span data-ttu-id="1dbf6-125">這個表單將是您的 MDI 子表單範本。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-125">This form will be the template for your MDI child forms.</span></span>  
  
     <span data-ttu-id="1dbf6-126">**Windows Form 設計工具**隨即開啟，顯示**Form2**。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-126">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>  
  
6. <span data-ttu-id="1dbf6-127">從**工具箱**，拖曳**RichTextBox**控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-127">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>  
  
7. <span data-ttu-id="1dbf6-128">在**屬性**視窗中，將`Anchor`屬性設**左上**而`Dock`屬性設**填滿**。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-128">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>  
  
     <span data-ttu-id="1dbf6-129">如此一來，<xref:System.Windows.Forms.RichTextBox> 控制項就會完全填滿 MDI 子表單區域，即使表單大小重新調整過亦可。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-129">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>  
  
8. <span data-ttu-id="1dbf6-130">按兩下**的新** 功能表項目，以建立<xref:System.Windows.Forms.Control.Click>為它的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-130">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>  
  
9. <span data-ttu-id="1dbf6-131">插入程式碼如下所示來建立新的 MDI 子表單，當使用者按一下**新增**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-131">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1dbf6-132">在下列範例中，事件處理常式會處理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-132">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="1dbf6-133">請注意，根據您的應用程式架構的細節您**新增**功能表項目可能無法`MenuItem2`。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-133">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     <span data-ttu-id="1dbf6-134">在 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] 中，將下列 `#include` 指示詞加入 Form1.h 上方：</span><span class="sxs-lookup"><span data-stu-id="1dbf6-134">In [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], add the following `#include` directive at the top of Form1.h:</span></span>  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. <span data-ttu-id="1dbf6-135">在頂端的下拉式清單中**屬性** 視窗中，選取對應至功能表列**檔案**功能表列並將<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性 視窗<xref:System.Windows.Forms.ToolStripMenuItem>。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-135">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
     <span data-ttu-id="1dbf6-136">這可讓**視窗**功能表維護一份開啟的 MDI 子視窗，在作用中的子視窗旁邊的核取記號。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-136">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>  
  
11. <span data-ttu-id="1dbf6-137">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-137">Press F5 to run the application.</span></span> <span data-ttu-id="1dbf6-138">藉由選取**的新**從**檔案**功能表中，您可以建立新的 MDI 子表單，其中會保留在追蹤的**視窗**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-138">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1dbf6-139">在 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 父表單中，開啟同樣具有 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 子表單時，如果您已設定 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性 (並選擇性地設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性)，則功能表項目會自動合併。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-139">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="1dbf6-140">將上述兩個 <xref:System.Windows.Forms.MainMenu> 的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性和子表單的所有功能表項目設定為 <xref:System.Windows.Forms.MenuMerge.MergeItems>。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-140">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="1dbf6-141">接著再設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性，如此一來，來自兩個功能表的功能表項目即可依指定順序出現。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-141">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="1dbf6-142">再者，請記住，在關閉 MDI 父表單時，每個 MDI 子表單都會在 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件引發前，先引發 <xref:System.Windows.Forms.Form.Closing> 事件。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-142">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="1dbf6-143">只取消 MDI 子表單的 <xref:System.Windows.Forms.Form.Closing> 事件並無法避免引發 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件；不過，MDI 父表單之 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 引數現在會設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-143">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="1dbf6-144">您可以將 <xref:System.ComponentModel.CancelEventArgs> 引數設定為 `false`，以強制關閉 MDI 父表單和所有 MDI 子表單。</span><span class="sxs-lookup"><span data-stu-id="1dbf6-144">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbf6-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dbf6-145">See also</span></span>

- [<span data-ttu-id="1dbf6-146">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="1dbf6-146">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="1dbf6-147">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="1dbf6-147">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="1dbf6-148">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="1dbf6-148">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="1dbf6-149">如何：將資料傳送至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="1dbf6-149">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="1dbf6-150">如何：排列 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="1dbf6-150">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
