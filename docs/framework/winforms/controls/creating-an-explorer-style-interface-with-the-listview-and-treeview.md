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
ms.openlocfilehash: 73d3a0bef1ab075aee8e06f676ef17b853773552
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468060"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面
Visual Studio 的優點之一是時間的能夠建立專業的 Windows Forms 應用程式在短量。 常見的案例建立使用者介面 (UI) 與<xref:System.Windows.Forms.ListView>和<xref:System.Windows.Forms.TreeView>類似於 Windows 作業系統的 Windows 檔案總管功能的控制項。 Windows 檔案總管會顯示使用者的電腦上的檔案和資料夾的階層式結構。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>若要建立包含 ListView 和 TreeView 控制項的表單  
  
1.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
2.  在 **新的專案**對話方塊方塊中，執行下列動作：  
  
    1.  在類別，選擇**Visual Basic**或是**Visual C#**。  
  
    2.  在範本清單中，選擇**Windows Forms 應用程式**。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。 建立新的 Windows Forms 專案。  
  
4.  新增<xref:System.Windows.Forms.SplitContainer>控制項至表單，並將其<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。  
  
5.  新增<xref:System.Windows.Forms.ImageList>名為`imageList1`至表單，並使用 [屬性] 視窗，以新增兩個映像： 資料夾映像和文件影像，依此順序。  
  
6.  新增<xref:System.Windows.Forms.TreeView>控制項，名為`treeview1`至表單，並將它的左邊<xref:System.Windows.Forms.SplitContainer>控制項。 在 [屬性] 視窗中`treeView1`執行下列動作：  
  
    1.  將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
    2.  將 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性設定為 `imagelist1.`  
  
7.  新增<xref:System.Windows.Forms.ListView>控制項，名為`listView1`至表單，並將其放置在右邊<xref:System.Windows.Forms.SplitContainer>控制項。 在 [屬性] 視窗中`listview1`執行下列動作：  
  
    1.  將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
    2.  將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View.Details>。  
  
    3.  開啟 [ColumnHeader 集合編輯器] 中，依序按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 中<xref:System.Windows.Forms.ListView.Columns%2A>屬性 **。** 新增三個資料行並設定其<xref:System.Windows.Forms.ColumnHeader.Text%2A>屬性，以`Name`， `Type`，和`Last Modified`分別。 按一下 [確定]  關閉對話方塊。  
  
    4.  將 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 屬性設定為 `imageList1.`  
  
8.  實作程式碼來填入<xref:System.Windows.Forms.TreeView>節點與子節點。 新增下列程式碼`Form1`類別。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. 由於先前的程式碼會使用 System.IO 命名空間，加入適當的使用，或匯入陳述式，在表單頂端。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. 從上一個步驟，在表單的建構函式呼叫設定方法或<xref:System.Windows.Forms.Form.Load>事件處理方法。 此程式碼加入表單的建構函式。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. 處理<xref:System.Windows.Forms.TreeView.NodeMouseClick>事件`treeview1` **，** 和實作程式碼來填入`listview1`按一下節點時，節點的內容。 新增下列程式碼`Form1`類別。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     如果您使用的 C#，請確定您有<xref:System.Windows.Forms.TreeView.NodeMouseClick>與其事件處理方法相關聯的事件。 此程式碼加入表單的建構函式。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試表單，以確定它如預期般運作。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
-   按 F5 執行應用程式。  
  
     您會看到一個分割形式，其中包含<xref:System.Windows.Forms.TreeView>左側，顯示您的專案目錄的控制項和<xref:System.Windows.Forms.ListView>具有三個資料行右側的控制項。 您可以周遊<xref:System.Windows.Forms.TreeView>藉由選取的目錄節點和<xref:System.Windows.Forms.ListView>會填入所選目錄的內容。  
  
## <a name="next-steps"></a>後續步驟  
 此應用程式可讓您的方式，您可以使用範例<xref:System.Windows.Forms.TreeView>和<xref:System.Windows.Forms.ListView>一起控制。 如需有關這些控制項的詳細資訊，請參閱下列主題：  
  
-   [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [操作說明：將搜尋能力加入至 ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [操作說明：將捷徑功能表附加至 TreeView 節點](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [操作說明：使用 Windows Forms TreeView 控制項加入和移除節點](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [操作說明：將資料行加入至 Windows Forms ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
