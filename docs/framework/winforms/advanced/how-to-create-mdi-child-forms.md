---
title: 如何：建立 MDI 子表單
description: 瞭解如何使用 Visual Studio 建立會顯示 RichTextBox 控制項的多重文件介面（MDI）子表單。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903177"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="71747-103">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="71747-103">How to: Create MDI child forms</span></span>

<span data-ttu-id="71747-104">MDI 子表單是[多重文件介面（MDI）應用程式](multiple-document-interface-mdi-applications.md)的重要元素，因為這些形式是使用者互動的中心。</span><span class="sxs-lookup"><span data-stu-id="71747-104">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="71747-105">在下列程式中，您將使用 Visual Studio 來建立顯示控制項的 MDI 子表單 <xref:System.Windows.Forms.RichTextBox> ，類似于大部分的文字處理應用程式。</span><span class="sxs-lookup"><span data-stu-id="71747-105">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="71747-106">藉由將 <xref:System.Windows.Forms> 控制項替換為其他控制項（例如 <xref:System.Windows.Forms.DataGridView> 控制項）或控制項的混合，您可以建立具有各種可能性的 MDI 子視窗（以及擴充功能、mdi 應用程式）。</span><span class="sxs-lookup"><span data-stu-id="71747-106">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="71747-107">建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="71747-107">Create MDI child forms</span></span>

1. <span data-ttu-id="71747-108">在 Visual Studio 中建立新的 Windows Forms 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="71747-108">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="71747-109">在表單的 [**屬性**] 視窗中，將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設為，並將 `true` 其屬性設定 `WindowsState` 為 `Maximized` 。</span><span class="sxs-lookup"><span data-stu-id="71747-109">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="71747-110">如此即可將表單指定為子視窗的 MDI 容器。</span><span class="sxs-lookup"><span data-stu-id="71747-110">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="71747-111">將 <xref:System.Windows.Forms.MenuStrip> 控制項從 [`Toolbox`] 拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="71747-111">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="71747-112">將其 `Text` 屬性設為**File**。</span><span class="sxs-lookup"><span data-stu-id="71747-112">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="71747-113">按一下 [**專案**] 屬性旁的省略號（...），然後按一下 [**新增**] 以加入兩個子工具區域的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="71747-113">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="71747-114">將 `Text` 這些專案的屬性設定為 [**新增**] 和 [**視窗]**。</span><span class="sxs-lookup"><span data-stu-id="71747-114">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="71747-115">在 [方案總管]\*\*\*\* 中，以滑鼠右鍵按一下專案，然後選取 [新增]\*\*\*\* > [新項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="71747-115">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="71747-116">在 [**加入新專案**] 對話方塊中，從 [**範本**] 窗格選取 [ **Windows Form** ] （在 Visual Basic 或 Visual c # 中）或 [ **Windows Forms 應用程式（.net）** ] （在 Visual C++ 中）。</span><span class="sxs-lookup"><span data-stu-id="71747-116">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="71747-117">在 [**名稱**] 方塊中，將表單命名為**Form2**。</span><span class="sxs-lookup"><span data-stu-id="71747-117">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="71747-118">選取 [**開啟**]，將表單新增至專案。</span><span class="sxs-lookup"><span data-stu-id="71747-118">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="71747-119">您在這個步驟中所建立的 MDI 子表單是標準的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="71747-119">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="71747-120">因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性，可讓您控制表單的透明度。</span><span class="sxs-lookup"><span data-stu-id="71747-120">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="71747-121">然而，<xref:System.Windows.Forms.Form.Opacity%2A> 屬性是專為最上層視窗而設計的。</span><span class="sxs-lookup"><span data-stu-id="71747-121">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="71747-122">請勿搭配 MDI 子表單使用這個屬性，這樣做可能會發生繪製問題。</span><span class="sxs-lookup"><span data-stu-id="71747-122">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="71747-123">這個表單將是您的 MDI 子表單範本。</span><span class="sxs-lookup"><span data-stu-id="71747-123">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="71747-124">**Windows Form 設計工具**隨即開啟，並顯示**Form2**。</span><span class="sxs-lookup"><span data-stu-id="71747-124">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="71747-125">從 [**工具箱**] 將 [ **RichTextBox** ] 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="71747-125">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="71747-126">在 [**屬性**] 視窗中，將 `Anchor` 屬性設定為**Top、Left** ，以及 `Dock` 要**填入**的屬性。</span><span class="sxs-lookup"><span data-stu-id="71747-126">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="71747-127">如此一來，<xref:System.Windows.Forms.RichTextBox> 控制項就會完全填滿 MDI 子表單區域，即使表單大小重新調整過亦可。</span><span class="sxs-lookup"><span data-stu-id="71747-127">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="71747-128">按兩下 [**新增**] 功能表項目，為 <xref:System.Windows.Forms.Control.Click> 其建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="71747-128">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="71747-129">插入與下列類似的程式碼，以便在使用者按一下 [**新增**] 功能表項目時建立新的 MDI 子表單。</span><span class="sxs-lookup"><span data-stu-id="71747-129">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="71747-130">在下列範例中，事件處理常式會處理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="71747-130">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="71747-131">請注意，視應用程式架構的細節而定，您的**新**功能表項目可能不是 `MenuItem2` 。</span><span class="sxs-lookup"><span data-stu-id="71747-131">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

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

   <span data-ttu-id="71747-132">在 c + + 中，于 Form1 的頂端新增下列指示詞 `#include` ：</span><span class="sxs-lookup"><span data-stu-id="71747-132">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="71747-133">在 [**屬性**] 視窗頂端的下拉式清單中，選取對應至 [檔案 **] 功能表區域的功能表區域**，並將屬性設定 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 為視窗 <xref:System.Windows.Forms.ToolStripMenuItem> 。</span><span class="sxs-lookup"><span data-stu-id="71747-133">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="71747-134">這可讓 [**視窗]** 功能表使用作用中子視窗旁的核取記號，維護開啟的 MDI 子視窗清單。</span><span class="sxs-lookup"><span data-stu-id="71747-134">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="71747-135">按**F5**執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="71747-135">Press **F5** to run the application.</span></span> <span data-ttu-id="71747-136">藉由從 [檔案] 功能表選取 [**新增**]，您可以建立新的 MDI 子表單，其會在 [**視窗]** **功能表項目**中保持追蹤。</span><span class="sxs-lookup"><span data-stu-id="71747-136">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="71747-137">在 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 父表單中，開啟同樣具有 <xref:System.Windows.Forms.MainMenu> 元件 (這個元件通常具有功能表項目的功能表結構) 的 MDI 子表單時，如果您已設定 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性 (並選擇性地設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性)，則功能表項目會自動合併。</span><span class="sxs-lookup"><span data-stu-id="71747-137">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="71747-138">將上述兩個 <xref:System.Windows.Forms.MainMenu> 的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性和子表單的所有功能表項目設定為 <xref:System.Windows.Forms.MenuMerge.MergeItems>。</span><span class="sxs-lookup"><span data-stu-id="71747-138">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="71747-139">接著再設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性，如此一來，來自兩個功能表的功能表項目即可依指定順序出現。</span><span class="sxs-lookup"><span data-stu-id="71747-139">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="71747-140">再者，請記住，在關閉 MDI 父表單時，每個 MDI 子表單都會在 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件引發前，先引發 <xref:System.Windows.Forms.Form.Closing> 事件。</span><span class="sxs-lookup"><span data-stu-id="71747-140">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="71747-141">只取消 MDI 子表單的 <xref:System.Windows.Forms.Form.Closing> 事件並無法避免引發 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件；不過，MDI 父表單之 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 引數現在會設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="71747-141">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="71747-142">您可以將 <xref:System.ComponentModel.CancelEventArgs> 引數設定為 `false`，以強制關閉 MDI 父表單和所有 MDI 子表單。</span><span class="sxs-lookup"><span data-stu-id="71747-142">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="71747-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71747-143">See also</span></span>

- [<span data-ttu-id="71747-144">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="71747-144">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="71747-145">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="71747-145">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="71747-146">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="71747-146">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="71747-147">如何：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="71747-147">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="71747-148">如何：安排 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="71747-148">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
