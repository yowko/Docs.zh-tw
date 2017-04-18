---
title: "逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "檔案總管樣式應用程式"
  - "檔案總管樣式應用程式, 逐步解說"
  - "ListView 控制項 [Windows Form], 檔案總管樣式介面"
  - "ListView 控制項 [Windows Form], 檔案總管樣式介面"
  - "ListView 控制項 [Windows Form], 一起使用的 TreeView 控制項"
  - "TreeView 控制項 [Windows Form], 一起使用的 ListView 控制項"
  - "TreeView 控制項 [Windows Form], 使用檔案總管樣式介面"
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 逐步解說：使用設計工具以 ListView 和 TreeView 控制項建立檔案總管風格的介面
Visual Studio 的其中一項優點，是能夠在短時間內建立外觀專業的 Windows Form 應用程式。  常見的案例是使用 <xref:System.Windows.Forms.ListView> 和 <xref:System.Windows.Forms.TreeView> 控制項來建立使用者介面 \(UI\)，這些控制項與 Windows 作業系統的 \[Windows 檔案總管\] 功能相似。  \[Windows 檔案總管\] 會顯示使用者電腦上檔案和資料夾的階層式結構。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立包含 ListView 和 TreeView 控制項的表單  
  
1.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，執行下列動作：  
  
    1.  在 \[分類\] 中，選擇 \[**Visual Basic**\] 或 \[**Visual C\#**\]。  
  
    2.  在範本清單中，選擇 \[**Windows Form 應用程式**\]。  
  
3.  按一下 \[**確定**\]。  新的 Windows Form 專案隨即建立。  
  
4.  將 <xref:System.Windows.Forms.SplitContainer> 控制項加入至表單，並將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>。  
  
5.  將名為 `imageList1` 的 <xref:System.Windows.Forms.ImageList> 加入至表單，並使用 \[屬性\] 視窗加入兩個影像：資料夾影像和文件影像 \(依此順序\)。  
  
6.  將名為 `treeview1` 的 <xref:System.Windows.Forms.TreeView> 控制項加入至表單，並將它放置在 <xref:System.Windows.Forms.SplitContainer> 控制項的左邊。  在 `treeView1` 的 \[屬性\] 視窗中，執行下列操作：  
  
    1.  將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle>。  
  
    2.  將 <xref:System.Windows.Forms.TreeView.ImageList%2A> 屬性設為 `imagelist1.`  
  
7.  將名為 `listView1` 的 <xref:System.Windows.Forms.ListView> 控制項加入至表單，並將它放置在 <xref:System.Windows.Forms.SplitContainer> 控制項的右邊。  在 `listview1` 的 \[屬性\] 視窗中，執行下列操作：  
  
    1.  將 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle>。  
  
    2.  將 <xref:System.Windows.Forms.ListView.View%2A> 屬性設定為 <xref:System.Windows.Forms.View>。  
  
    3.  按一下 <xref:System.Windows.Forms.ListView.Columns%2A> 屬性中的省略符號 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)，藉此開啟 \[ColumnHeader 集合編輯器\]。 加入三個資料行，並將它們的 <xref:System.Windows.Forms.ColumnHeader.Text%2A> 屬性分別設定為 `Name`、`Type` 和 `Last Modified`。  按一下 \[**確定**\] 以關閉對話方塊。  
  
    4.  將 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 屬性設定為 `imageList1.`  
  
8.  實作程式碼，以節點和子節點填入 <xref:System.Windows.Forms.TreeView>。  將此程式碼加入至 `Form1` 類別。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. 由於之前的程式碼是使用 System.IO 命名空間 \(Namespace\)，因此請加入適當的使用，或是在表單頂端位置匯入陳述式 \(Statement\)。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. 在表單建構函式中呼叫上一個步驟的設定方法或 <xref:System.Windows.Forms.Form.Load> 事件處理方法。  將此程式碼加入至表單建構函式。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. 處理 `treeview1` 的 <xref:System.Windows.Forms.TreeView.NodeMouseClick> 事件，並實作程式碼，在按一下節點時以節點的內容填入 `listview1`。  將此程式碼加入至 `Form1` 類別。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     如果您是使用 C\#，請確定已將 <xref:System.Windows.Forms.TreeView.NodeMouseClick> 事件與其事件處理方法相關聯。  將此程式碼加入至表單建構函式。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## 測試應用程式  
 您現在可以測試表單以確定它的行為表現如預期般。  
  
#### 若要測試表單  
  
-   按下 F5 執行應用程式。  
  
     您將會看到分隔表單，其中包含 <xref:System.Windows.Forms.TreeView> 控制項，該控制項會在左邊顯示您的專案目錄，另外還有一個 <xref:System.Windows.Forms.ListView> 控制項，該控制項位在右邊且擁有三個資料行。  您可以藉由選取目錄節點來周遊 <xref:System.Windows.Forms.TreeView>，而 <xref:System.Windows.Forms.ListView> 中會填入選取的目錄內容。  
  
## 後續步驟  
 這個應用程式提供您可以同時使用 <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> 控制項的方法案例。  如需這些控制項的詳細資訊，請參閱下列主題：  
  
-   [如何：將自訂資訊加入 TreeView 或 ListView 控制項 \(Windows Form\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [如何：將搜尋能力加入至 ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [如何：將捷徑功能表附加至 TreeView 節點](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## 請參閱  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.TreeView>   
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [如何：使用 Windows Form TreeView 控制項加入和移除節點](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)   
 [如何：使用 Windows Form ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [如何：將資料行加入至 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)