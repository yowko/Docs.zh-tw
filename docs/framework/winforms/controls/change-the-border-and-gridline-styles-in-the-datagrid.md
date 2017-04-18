---
title: "如何：變更 Windows Form DataGridView 控制項中的框線和格線樣式 | Microsoft Docs"
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
  - "資料格, 變更框線樣式"
  - "資料格, 變更格線樣式"
  - "DataGridView 控制項 [Windows Form], 框線樣式"
  - "DataGridView 控制項 [Windows Form], 格線樣式"
  - "格線, 變更樣式"
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：變更 Windows Form DataGridView 控制項中的框線和格線樣式
您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項自訂控制項的框線和格線的外觀，以改進使用者經歷。  除了控制項中儲存格的框線樣式之外，還可以修改格線色彩和控制項框線樣式。  也可以針對一般儲存格、資料列行首儲存格，以及資料行行首儲存格套用不同的儲存格框線樣式。  
  
> [!NOTE]
>  格線色彩只能用於 <xref:System.Windows.Forms.DataGridViewCellBorderStyle> 列舉型別的 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>、<xref:System.Windows.Forms.DataGridViewCellBorderStyle> 和 <xref:System.Windows.Forms.DataGridViewCellBorderStyle> 值以及 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> 列舉型別的 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> 值。  這些列舉型別的其他值則使用由作業系統所指定的色彩。  此外，當透過 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> 方法啟用 Windows XP 和 Windows Server 2003 系列的視覺化樣式時，不會使用 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性值。  
  
### 若要以程式設計方式變更格線色彩  
  
-   設定 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### 若要以程式設計方式變更整個 DataGridView 控制項的框線樣式  
  
-   將 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.BorderStyle> 列舉值。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### 若要以程式設計方式變更 DataGridView 儲存格的框線樣式  
  
-   設定 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>、<xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName> 和 <xref:System.Drawing?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.BorderStyle>   
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>   
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>   
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)