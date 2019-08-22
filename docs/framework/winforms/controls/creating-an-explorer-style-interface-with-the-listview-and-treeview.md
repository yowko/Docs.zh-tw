---
title: 逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面
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
ms.openlocfilehash: d80f8e3bc729689b274af520bc37fda8417b0407
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658575"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面

Visual Studio 的優點之一, 就是能夠在短時間內建立專業型式的 Windows Forms 應用程式。 常見的案例是使用<xref:System.Windows.Forms.ListView>和<xref:System.Windows.Forms.TreeView>控制項來建立使用者介面 (UI), 這與 windows 作業系統的 windows Explorer 功能相似。 Windows Explorer 會顯示使用者電腦上檔案和資料夾的階層式結構。

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>建立包含 ListView 和 TreeView 控制項的表單

1. 在 [檔案] 功能表中，指向 [新增]，然後按一下 [專案]。

2. 在 [**新增專案**] 對話方塊中, 執行下列動作:

    1. 在 [類別] 中, 選擇 [ **Visual Basic** ] 或 [**視覺效果C#** ]。

    2. 在範本清單中, 選擇 [ **Windows Forms 應用程式**]。

3. 按一下 [確定]。 隨即建立新的 Windows Forms 專案。

4. 將控制項新增至表單, 並將<xref:System.Windows.Forms.SplitContainer.Dock%2A>其屬性設定為<xref:System.Windows.Forms.DockStyle.Fill>。 <xref:System.Windows.Forms.SplitContainer>

5. <xref:System.Windows.Forms.ImageList>將名`imageList1`為的新增至表單, 並使用屬性視窗來新增兩個影像: 資料夾影像和檔影像 (依該順序)。

6. 將名`treeview1`為的<xref:System.Windows.Forms.SplitContainer>控制項新增至表單, 並將它放在控制項的左側。 <xref:System.Windows.Forms.TreeView> 在 [屬性視窗`treeView1` ] 中, 執行下列動作:

    1. 將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。

    2. 將 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性設定為 `imagelist1.`

7. 將名`listView1`為的<xref:System.Windows.Forms.SplitContainer>控制項新增至表單, 並將它放在控制項的右側。 <xref:System.Windows.Forms.ListView> 在 [屬性視窗`listview1` ] 中, 執行下列動作:

    1. 將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。

    2. 將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View.Details>。

    3. 按一下![屬性<xref:System.Windows.Forms.ListView.Columns%2A>中的省略號 (](./media/visual-studio-ellipsis-button.png)Visual Studio 屬性視窗中的省略號按鈕 (...), 以開啟 [ColumnHeader 集合編輯器] **。** 新增三個數據行, <xref:System.Windows.Forms.ColumnHeader.Text%2A>並分別`Name`將其屬性`Last Modified`設為、 `Type`和。 按一下 [確定] 關閉對話方塊。

    4. 將 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 屬性設定為 `imageList1.`

8. 執行程式碼, 以<xref:System.Windows.Forms.TreeView>使用節點和子節點填入。 將此程式碼新增`Form1`至類別。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. 由於先前的程式碼會使用 System.IO 命名空間, 請在表單頂端新增適當的 using 或 import 語句。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. 在表單的函式或<xref:System.Windows.Forms.Form.Load>事件處理方法中, 從上一個步驟呼叫設定方法。 將此程式碼新增至表單的函式。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. `listview1`處理的<xref:System.Windows.Forms.TreeView.NodeMouseClick> `treeview1`事件, 並在按一下節點時 **,** 執行程式碼以填入節點的內容。 將此程式碼新增`Form1`至類別。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     如果您使用C#的是, 請確定您有<xref:System.Windows.Forms.TreeView.NodeMouseClick>與其事件處理方法相關聯的事件。 將此程式碼新增至表單的函式。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a>測試應用程式

您現在可以測試表單, 以確定它會如預期般運作。

#### <a name="to-test-the-form"></a>測試表單

- 按 F5 執行應用程式。

     您會看到一個分割表單, <xref:System.Windows.Forms.TreeView>其中包含一個控制項, 它會在左側顯示您的專案<xref:System.Windows.Forms.ListView>目錄, 並在右側有三個數據行的控制項。 您可以<xref:System.Windows.Forms.TreeView>藉由選取 [目錄節點] 來進行<xref:System.Windows.Forms.ListView>流覽, 並填入所選目錄的內容。

## <a name="next-steps"></a>後續步驟

此應用程式提供您可搭配使用<xref:System.Windows.Forms.TreeView>和<xref:System.Windows.Forms.ListView>控制項的方式範例。 如需這些控制項的詳細資訊, 請參閱下列主題:

- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [如何：將搜尋功能新增至 ListView 控制項](how-to-add-search-capabilities-to-a-listview-control.md)

- [如何：將快捷方式功能表附加至 TreeView 節點](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [ListView 控制項](listview-control-windows-forms.md)
- [如何：使用 Windows Forms TreeView 控制項加入和移除節點](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [如何：使用 Windows Forms ListView 控制項新增和移除專案](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [如何：將資料行新增至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
