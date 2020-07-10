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
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面

Visual Studio 的優點之一，就是能夠在短時間內建立專業型式的 Windows Forms 應用程式。 常見的案例是使用 <xref:System.Windows.Forms.ListView> 和 <xref:System.Windows.Forms.TreeView> 控制項（類似 windows 作業系統的 windows Explorer 功能）來建立使用者介面 (UI) 。 Windows Explorer 會顯示使用者電腦上檔案和資料夾的階層式結構。

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>建立包含 ListView 和 TreeView 控制項的表單

1. 在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。

2. 在 [新增專案] **** 對話方塊中，執行下列操作：

    1. 在 [類別] 中，選擇 [ **Visual Basic** ] 或 [ **Visual c #**]。

    2. 在範本清單中，選擇 [ **Windows Forms 應用程式**]。

3. 按一下 [確定]。 隨即建立新的 Windows Forms 專案。

4. 將 <xref:System.Windows.Forms.SplitContainer> 控制項新增至表單，並將其 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill> 。

5. 將 <xref:System.Windows.Forms.ImageList> 名為 `imageList1` 的新增至表單，並使用屬性視窗來新增兩個影像：資料夾影像和檔影像（依該順序）。

6. 將 <xref:System.Windows.Forms.TreeView> 名為的控制項新增 `treeview1` 至表單，並將它放在控制項的左側 <xref:System.Windows.Forms.SplitContainer> 。 在 [屬性視窗] 中 `treeView1` ，執行下列動作：

    1. 將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。

    2. 將 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性設定為 `imagelist1.`

7. 將 <xref:System.Windows.Forms.ListView> 名為的控制項新增 `listView1` 至表單，並將它放在控制項的右側 <xref:System.Windows.Forms.SplitContainer> 。 在 [屬性視窗] 中 `listview1` ，執行下列動作：

    1. 將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。

    2. 將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設為 <xref:System.Windows.Forms.View.Details>。

    3. 在屬性的 Visual Studio 屬性視窗中，按一下 ![ 省略號按鈕 ( ( ... ) ，以開啟 [ColumnHeader 集合編輯器]。 ](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.ListView.Columns%2A> **.** 新增三個數據行，並分別將其 <xref:System.Windows.Forms.ColumnHeader.Text%2A> 屬性設為 `Name` 、 `Type` 和 `Last Modified` 。 按一下 [確定]  關閉對話方塊。

    4. 將 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 屬性設定為 `imageList1.`

8. 執行程式碼，以 <xref:System.Windows.Forms.TreeView> 使用節點和子節點填入。 將此程式碼新增至 `Form1` 類別。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. 由於先前的程式碼會使用 System.IO 命名空間，請在表單頂端新增適當的 using 或 import 語句。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. 在表單的函 <xref:System.Windows.Forms.Form.Load> 式或事件處理方法中，從上一個步驟呼叫設定方法。 將此程式碼新增至表單的函式。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. 處理的 <xref:System.Windows.Forms.TreeView.NodeMouseClick> 事件 `treeview1` **，** 並在按一下節點時，執行程式碼以填入 `listview1` 節點的內容。 將此程式碼新增至 `Form1` 類別。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     如果您使用的是 c #，請確定您有與其 <xref:System.Windows.Forms.TreeView.NodeMouseClick> 事件處理方法相關聯的事件。 將此程式碼新增至表單的函式。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a>測試應用程式

您現在可以測試表單，以確定它會如預期般運作。

#### <a name="to-test-the-form"></a>測試表單

- 按 F5 執行應用程式。

     您會看到一個分割表單，其中包含一個 <xref:System.Windows.Forms.TreeView> 控制項，它會在左側顯示您的專案目錄，並在 <xref:System.Windows.Forms.ListView> 右側有三個數據行的控制項。 您可以藉由選取 [目錄節點] 來進行流覽 <xref:System.Windows.Forms.TreeView> ，並 <xref:System.Windows.Forms.ListView> 填入所選目錄的內容。

## <a name="next-steps"></a>後續步驟

此應用程式提供您可搭配使用和控制項的方式 <xref:System.Windows.Forms.TreeView> 範例 <xref:System.Windows.Forms.ListView> 。 如需這些控制項的詳細資訊，請參閱下列主題：

- [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [如何：將搜尋能力加入至 ListView 控制項](how-to-add-search-capabilities-to-a-listview-control.md)

- [操作說明：將捷徑功能表附加至 TreeView 節點](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [ListView 控制項](listview-control-windows-forms.md)
- [如何：使用 Windows Form TreeView 控制項加入和移除節點](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [操作說明：將資料行加入至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
