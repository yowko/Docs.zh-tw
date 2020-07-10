---
title: 逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面
description: 瞭解如何使用設計工具建立具有 Windows Forms ListView 和 TreeView 控制項的 Explorer 樣式介面。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: 44d4db1ef3da85dbf411498f486882b86a05c140
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174623"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="0e450-103">逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面</span><span class="sxs-lookup"><span data-stu-id="0e450-103">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>

<span data-ttu-id="0e450-104">Visual Studio 的優點之一，就是能夠在短時間內建立專業型式的 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e450-104">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="0e450-105">常見的案例是使用 <xref:System.Windows.Forms.ListView> 和 <xref:System.Windows.Forms.TreeView> 控制項（類似 windows 作業系統的 windows Explorer 功能）來建立使用者介面 (UI) 。</span><span class="sxs-lookup"><span data-stu-id="0e450-105">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="0e450-106">Windows Explorer 會顯示使用者電腦上檔案和資料夾的階層式結構。</span><span class="sxs-lookup"><span data-stu-id="0e450-106">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="0e450-107">建立包含 ListView 和 TreeView 控制項的表單</span><span class="sxs-lookup"><span data-stu-id="0e450-107">To create the form containing a ListView and TreeView control</span></span>

1. <span data-ttu-id="0e450-108">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="0e450-108">On the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="0e450-109">在 [新增專案] \*\*\*\* 對話方塊中，執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="0e450-109">In the **New Project** dialog box, do the following:</span></span>

    1. <span data-ttu-id="0e450-110">在 [類別] 中，選擇 [ **Visual Basic** ] 或 [ **Visual c #**]。</span><span class="sxs-lookup"><span data-stu-id="0e450-110">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>

    2. <span data-ttu-id="0e450-111">在範本清單中，選擇 [ **Windows Forms 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="0e450-111">In the list of templates, choose **Windows Forms Application**.</span></span>

3. <span data-ttu-id="0e450-112">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0e450-112">Click **OK**.</span></span> <span data-ttu-id="0e450-113">隨即建立新的 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="0e450-113">A new Windows Forms project is created.</span></span>

4. <span data-ttu-id="0e450-114">將 <xref:System.Windows.Forms.SplitContainer> 控制項新增至表單，並將其 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill> 。</span><span class="sxs-lookup"><span data-stu-id="0e450-114">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="0e450-115">將 <xref:System.Windows.Forms.ImageList> 名為 `imageList1` 的新增至表單，並使用屬性視窗來新增兩個影像：資料夾影像和檔影像（依該順序）。</span><span class="sxs-lookup"><span data-stu-id="0e450-115">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>

6. <span data-ttu-id="0e450-116">將 <xref:System.Windows.Forms.TreeView> 名為的控制項新增 `treeview1` 至表單，並將它放在控制項的左側 <xref:System.Windows.Forms.SplitContainer> 。</span><span class="sxs-lookup"><span data-stu-id="0e450-116">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="0e450-117">在 [屬性視窗] 中 `treeView1` ，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0e450-117">In the Properties window for `treeView1` do the following:</span></span>

    1. <span data-ttu-id="0e450-118">將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="0e450-118">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="0e450-119">將 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性設定為 `imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="0e450-119">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>

7. <span data-ttu-id="0e450-120">將 <xref:System.Windows.Forms.ListView> 名為的控制項新增 `listView1` 至表單，並將它放在控制項的右側 <xref:System.Windows.Forms.SplitContainer> 。</span><span class="sxs-lookup"><span data-stu-id="0e450-120">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="0e450-121">在 [屬性視窗] 中 `listview1` ，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0e450-121">In the Properties window for `listview1` do the following:</span></span>

    1. <span data-ttu-id="0e450-122">將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="0e450-122">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="0e450-123">將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設為 <xref:System.Windows.Forms.View.Details>。</span><span class="sxs-lookup"><span data-stu-id="0e450-123">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

    3. <span data-ttu-id="0e450-124">在屬性的 Visual Studio 屬性視窗中，按一下 ![ 省略號按鈕 ( ( ... ) ，以開啟 [ColumnHeader 集合編輯器]。 ](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.ListView.Columns%2A> **.**</span><span class="sxs-lookup"><span data-stu-id="0e450-124">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="0e450-125">新增三個數據行，並分別將其 <xref:System.Windows.Forms.ColumnHeader.Text%2A> 屬性設為 `Name` 、 `Type` 和 `Last Modified` 。</span><span class="sxs-lookup"><span data-stu-id="0e450-125">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="0e450-126">按一下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0e450-126">Click **OK** to close the dialog box.</span></span>

    4. <span data-ttu-id="0e450-127">將 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 屬性設定為 `imageList1.`</span><span class="sxs-lookup"><span data-stu-id="0e450-127">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>

8. <span data-ttu-id="0e450-128">執行程式碼，以 <xref:System.Windows.Forms.TreeView> 使用節點和子節點填入。</span><span class="sxs-lookup"><span data-stu-id="0e450-128">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="0e450-129">將此程式碼新增至 `Form1` 類別。</span><span class="sxs-lookup"><span data-stu-id="0e450-129">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. <span data-ttu-id="0e450-130">由於先前的程式碼會使用 System.IO 命名空間，請在表單頂端新增適當的 using 或 import 語句。</span><span class="sxs-lookup"><span data-stu-id="0e450-130">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. <span data-ttu-id="0e450-131">在表單的函 <xref:System.Windows.Forms.Form.Load> 式或事件處理方法中，從上一個步驟呼叫設定方法。</span><span class="sxs-lookup"><span data-stu-id="0e450-131">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="0e450-132">將此程式碼新增至表單的函式。</span><span class="sxs-lookup"><span data-stu-id="0e450-132">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <span data-ttu-id="0e450-133">處理的 <xref:System.Windows.Forms.TreeView.NodeMouseClick> 事件 `treeview1` **，** 並在按一下節點時，執行程式碼以填入 `listview1` 節點的內容。</span><span class="sxs-lookup"><span data-stu-id="0e450-133">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="0e450-134">將此程式碼新增至 `Form1` 類別。</span><span class="sxs-lookup"><span data-stu-id="0e450-134">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     <span data-ttu-id="0e450-135">如果您使用的是 c #，請確定您有與其 <xref:System.Windows.Forms.TreeView.NodeMouseClick> 事件處理方法相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="0e450-135">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="0e450-136">將此程式碼新增至表單的函式。</span><span class="sxs-lookup"><span data-stu-id="0e450-136">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a><span data-ttu-id="0e450-137">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="0e450-137">Testing the Application</span></span>

<span data-ttu-id="0e450-138">您現在可以測試表單，以確定它會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="0e450-138">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="0e450-139">測試表單</span><span class="sxs-lookup"><span data-stu-id="0e450-139">To test the form</span></span>

- <span data-ttu-id="0e450-140">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e450-140">Press F5 to run the application.</span></span>

     <span data-ttu-id="0e450-141">您會看到一個分割表單，其中包含一個 <xref:System.Windows.Forms.TreeView> 控制項，它會在左側顯示您的專案目錄，並在 <xref:System.Windows.Forms.ListView> 右側有三個數據行的控制項。</span><span class="sxs-lookup"><span data-stu-id="0e450-141">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="0e450-142">您可以藉由選取 [目錄節點] 來進行流覽 <xref:System.Windows.Forms.TreeView> ，並 <xref:System.Windows.Forms.ListView> 填入所選目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="0e450-142">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0e450-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0e450-143">Next Steps</span></span>

<span data-ttu-id="0e450-144">此應用程式提供您可搭配使用和控制項的方式 <xref:System.Windows.Forms.TreeView> 範例 <xref:System.Windows.Forms.ListView> 。</span><span class="sxs-lookup"><span data-stu-id="0e450-144">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="0e450-145">如需這些控制項的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="0e450-145">For more information on these controls, see the following topics:</span></span>

- [<span data-ttu-id="0e450-146">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0e450-146">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [<span data-ttu-id="0e450-147">如何：將搜尋能力加入至 ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="0e450-147">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)

- [<span data-ttu-id="0e450-148">操作說明：將捷徑功能表附加至 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="0e450-148">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a><span data-ttu-id="0e450-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e450-149">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="0e450-150">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="0e450-150">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="0e450-151">如何：使用 Windows Form TreeView 控制項加入和移除節點</span><span class="sxs-lookup"><span data-stu-id="0e450-151">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="0e450-152">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="0e450-152">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="0e450-153">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="0e450-153">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
