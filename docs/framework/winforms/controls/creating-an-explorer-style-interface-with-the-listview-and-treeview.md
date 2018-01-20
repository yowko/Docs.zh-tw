---
title: "逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面"
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
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d8d7991f706f8098e4ac475ae057771de200197
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="236ce-102">逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面</span><span class="sxs-lookup"><span data-stu-id="236ce-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>
<span data-ttu-id="236ce-103">其中一個 Visual Studio 的優點是時間的能夠建立專業的 Windows Form 應用程式在短量。</span><span class="sxs-lookup"><span data-stu-id="236ce-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="236ce-104">透過常見的案例所建立的使用者介面 (UI)<xref:System.Windows.Forms.ListView>和<xref:System.Windows.Forms.TreeView>類似於 Windows 作業系統的 Windows 檔案總管 功能的控制項。</span><span class="sxs-lookup"><span data-stu-id="236ce-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="236ce-105">Windows 檔案總管 會顯示使用者的電腦上的檔案和資料夾的階層式結構。</span><span class="sxs-lookup"><span data-stu-id="236ce-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="236ce-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="236ce-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="236ce-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="236ce-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="236ce-108">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="236ce-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="236ce-109">若要建立包含 ListView 和 TreeView 控制項的表單</span><span class="sxs-lookup"><span data-stu-id="236ce-109">To create the form containing a ListView and TreeView control</span></span>  
  
1.  <span data-ttu-id="236ce-110">在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。</span><span class="sxs-lookup"><span data-stu-id="236ce-110">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="236ce-111">在**新專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="236ce-111">In the **New Project** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="236ce-112">在類別中，選擇**Visual Basic**或**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="236ce-112">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>  
  
    2.  <span data-ttu-id="236ce-113">在範本清單中，選擇  **Windows Forms 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="236ce-113">In the list of templates, choose **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="236ce-114">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="236ce-114">Click **OK**.</span></span> <span data-ttu-id="236ce-115">建立新的 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="236ce-115">A new Windows Forms project is created.</span></span>  
  
4.  <span data-ttu-id="236ce-116">新增<xref:System.Windows.Forms.SplitContainer>控制項加入表單，並設定其<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="236ce-116">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="236ce-117">新增<xref:System.Windows.Forms.ImageList>名為`imageList1`至表單，並使用 [屬性] 視窗，將兩個映像： 資料夾影像，以及文件影像，依此順序。</span><span class="sxs-lookup"><span data-stu-id="236ce-117">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>  
  
6.  <span data-ttu-id="236ce-118">新增<xref:System.Windows.Forms.TreeView>控制項，名為`treeview1`表單，並將其放置在左邊<xref:System.Windows.Forms.SplitContainer>控制項。</span><span class="sxs-lookup"><span data-stu-id="236ce-118">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="236ce-119">在 [屬性] 視窗中`treeView1`執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="236ce-119">In the Properties window for `treeView1` do the following:</span></span>  
  
    1.  <span data-ttu-id="236ce-120">將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="236ce-120">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="236ce-121">將 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性設定為 `imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="236ce-121">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>  
  
7.  <span data-ttu-id="236ce-122">新增<xref:System.Windows.Forms.ListView>控制項，名為`listView1`表單，並將其放置在右邊<xref:System.Windows.Forms.SplitContainer>控制項。</span><span class="sxs-lookup"><span data-stu-id="236ce-122">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="236ce-123">在 [屬性] 視窗中`listview1`執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="236ce-123">In the Properties window for `listview1` do the following:</span></span>  
  
    1.  <span data-ttu-id="236ce-124">將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="236ce-124">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="236ce-125">將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View.Details>。</span><span class="sxs-lookup"><span data-stu-id="236ce-125">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
    3.  <span data-ttu-id="236ce-126">開啟屬於 ColumnHeader 集合編輯器，依序按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 中<xref:System.Windows.Forms.ListView.Columns%2A>屬性**。**</span><span class="sxs-lookup"><span data-stu-id="236ce-126">Open the ColumnHeader Collection Editor by clicking the ellipses (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the <xref:System.Windows.Forms.ListView.Columns%2A> property**.**</span></span> <span data-ttu-id="236ce-127">新增三個資料行並設定其<xref:System.Windows.Forms.ColumnHeader.Text%2A>屬性`Name`， `Type`，和`Last Modified`分別。</span><span class="sxs-lookup"><span data-stu-id="236ce-127">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="236ce-128">按一下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="236ce-128">Click **OK** to close the dialog box.</span></span>  
  
    4.  <span data-ttu-id="236ce-129">將 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 屬性設定為 `imageList1.`</span><span class="sxs-lookup"><span data-stu-id="236ce-129">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>  
  
8.  <span data-ttu-id="236ce-130">實作程式碼以填入<xref:System.Windows.Forms.TreeView>節點與子節點。</span><span class="sxs-lookup"><span data-stu-id="236ce-130">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="236ce-131">將此程式碼加入`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="236ce-131">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. <span data-ttu-id="236ce-132">因為先前的程式碼使用 System.IO 命名空間，加入適當的使用，或匯入陳述式，在表單頂端。</span><span class="sxs-lookup"><span data-stu-id="236ce-132">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="236ce-133">從上一個步驟中表單的建構函式呼叫設定方法或<xref:System.Windows.Forms.Form.Load>事件處理方法。</span><span class="sxs-lookup"><span data-stu-id="236ce-133">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="236ce-134">將此程式碼加入至表單的建構函式。</span><span class="sxs-lookup"><span data-stu-id="236ce-134">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. <span data-ttu-id="236ce-135">處理<xref:System.Windows.Forms.TreeView.NodeMouseClick>事件`treeview1` **，**和實作程式碼以填入`listview1`與節點的內容時按一下節點。</span><span class="sxs-lookup"><span data-stu-id="236ce-135">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="236ce-136">將此程式碼加入`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="236ce-136">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     <span data-ttu-id="236ce-137">如果您使用的 C#，請確定您有<xref:System.Windows.Forms.TreeView.NodeMouseClick>與其事件處理方法相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="236ce-137">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="236ce-138">將此程式碼加入至表單的建構函式。</span><span class="sxs-lookup"><span data-stu-id="236ce-138">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="236ce-139">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="236ce-139">Testing the Application</span></span>  
 <span data-ttu-id="236ce-140">您現在可以測試表單，以確定其如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="236ce-140">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="236ce-141">若要測試表單</span><span class="sxs-lookup"><span data-stu-id="236ce-141">To test the form</span></span>  
  
-   <span data-ttu-id="236ce-142">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="236ce-142">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="236ce-143">您會看到分割表單，其中包含<xref:System.Windows.Forms.TreeView>左側，顯示您的專案目錄的控制項和<xref:System.Windows.Forms.ListView>具有三個資料行右側的控制項。</span><span class="sxs-lookup"><span data-stu-id="236ce-143">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="236ce-144">您可以周遊<xref:System.Windows.Forms.TreeView>選取目錄節點和<xref:System.Windows.Forms.ListView>選取目錄的內容中會填入。</span><span class="sxs-lookup"><span data-stu-id="236ce-144">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="236ce-145">後續步驟</span><span class="sxs-lookup"><span data-stu-id="236ce-145">Next Steps</span></span>  
 <span data-ttu-id="236ce-146">此應用程式可讓您的方式，您可以使用範例<xref:System.Windows.Forms.TreeView>和<xref:System.Windows.Forms.ListView>控制在一起。</span><span class="sxs-lookup"><span data-stu-id="236ce-146">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="236ce-147">如需有關這些控制項的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="236ce-147">For more information on these controls, see the following topics:</span></span>  
  
-   [<span data-ttu-id="236ce-148">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="236ce-148">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [<span data-ttu-id="236ce-149">操作說明：將搜尋能力加入至 ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="236ce-149">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [<span data-ttu-id="236ce-150">操作說明：將捷徑功能表附加至 TreeView 節點</span><span class="sxs-lookup"><span data-stu-id="236ce-150">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a><span data-ttu-id="236ce-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="236ce-151">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [<span data-ttu-id="236ce-152">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="236ce-152">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="236ce-153">操作說明：使用 Windows Forms TreeView 控制項加入和移除節點</span><span class="sxs-lookup"><span data-stu-id="236ce-153">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="236ce-154">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="236ce-154">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="236ce-155">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="236ce-155">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
