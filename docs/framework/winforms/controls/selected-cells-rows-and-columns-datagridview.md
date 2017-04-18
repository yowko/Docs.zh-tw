---
title: "如何：取得 Windows Form DataGridView 控制項中選取的儲存格、資料列和資料行 | Microsoft Docs"
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
  - "DataGridView 控制項 [Windows Form], 取得選擇"
  - "取得選擇, DataGridView 控制項 [Windows Form]"
  - "選取範圍, DataGridView 控制項 [Windows Form]"
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：取得 Windows Form DataGridView 控制項中選取的儲存格、資料列和資料行
您可以自 <xref:System.Windows.Forms.DataGridView> 控制項取得選取的儲存格、資料列或資料行，方法是使用對應的屬性：<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>、<xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 和 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>。  在下列程序中，您將會取得選取的儲存格，並將資料列和資料行索引顯示於 <xref:System.Windows.Forms.MessageBox>。  
  
### 若要取得 DataGridView 控制項中選取的儲存格  
  
-   使用 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 屬性。  
  
    > [!NOTE]
    >  使用 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> 方法以防止顯示可能的大量儲存格。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### 若要取得 DataGridView 控制項中選取的資料列  
  
-   使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 屬性。  若要允許使用者選取資料列，您必須將 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode>。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### 若要取得 DataGridView 控制項中選取的資料列  
  
-   使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 屬性。  若要允許使用者選取資料行，您必須將 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode>。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `selectedCellsButton`、`selectedRowsButton` 和 `selectedColumnsButton` 的 <xref:System.Windows.Forms.Button> 控制項，每個控制項都具有附加 <xref:System.Windows.Forms.Control.Click> 事件的處理常式。  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName> 和 <xref:System.Text?displayProperty=fullName> 組件的參考。  
  
## 穩固程式設計  
 此章節中所描述的集合，在選取大量儲存格、資料列或資料行的情況下，執行起來會沒有效率。  如需在大量資料的情況下使用這些集合的詳細資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>   
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>   
 [選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)