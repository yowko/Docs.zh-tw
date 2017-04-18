---
title: "如何：依據 Windows Form DataGridView 控制項儲存格的變更執行自訂動作 | Microsoft Docs"
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
  - "儲存格, 偵測變更"
  - "資料格, 偵測儲存格中的變更"
  - "DataGridView 控制項 [Windows Form], 偵測儲存格中的變更"
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：依據 Windows Form DataGridView 控制項儲存格的變更執行自訂動作
<xref:System.Windows.Forms.DataGridView> 控制項具有許多事件，您可用這些事件來偵測在 <xref:System.Windows.Forms.DataGridView> 儲存格狀態中的變更。  最常用的兩個事件是 <xref:System.Windows.Forms.DataGridView.CellValueChanged> 和 <xref:System.Windows.Forms.DataGridView.CellStateChanged> 事件。  
  
### 若要偵測 DataGridView 儲存格值的變更  
  
-   撰寫 <xref:System.Windows.Forms.DataGridView.CellValueChanged> 事件的處理常式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### 若要偵測 DataGridView 儲存格狀態的變更  
  
-   撰寫 <xref:System.Windows.Forms.DataGridView.CellStateChanged> 事件的處理常式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  針對 C\#，事件處理常式必須要連接至對應的事件。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)   
 [逐步解說：驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)