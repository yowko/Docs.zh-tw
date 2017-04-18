---
title: "如何：格式化 Windows Form DataGridView 控制項中的資料 | Microsoft Docs"
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
  - "儲存格, 文字對齊"
  - "貨幣值, 在資料格中格式化"
  - "資料 [Windows Form], 在 DataGridView 控制項中格式化"
  - "資料格, 貨幣值"
  - "資料格, 日期值"
  - "資料格, 啟用自動換行"
  - "資料格, 格式化資料"
  - "資料格, 文字對齊"
  - "DataGridView 控制項 [Windows Form], 格式化資料"
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：格式化 Windows Form DataGridView 控制項中的資料
下列程序使用 <xref:System.Windows.Forms.DataGridView> 控制項以及控制項特定資料行的 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 屬性，示範儲存格值的基本格式化。  如需進階資料格式化的詳細資訊，請參閱 [如何：自訂 Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
### 若要格式化貨幣及日期值  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 屬性。  下列程式碼範例使用資料行的 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 屬性，設定特定資料行的格式。   `UnitPrice`  資料行中的值會顯示為目前文化特定的貨幣格式，具有由括號括住的負值。   `ShipDate`  資料行中的值會顯示為目前文化特定的簡短日期格式。  如需 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 值的詳細資訊，請參閱[格式化類型](../../../../docs/standard/base-types/formatting-types.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### 若要自訂 null 資料庫值的顯示  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 屬性。  下列程式碼範例使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> 屬性，在所有包含等於 <xref:System.DBNull.Value?displayProperty=fullName> 的值之儲存格中顯示 "no entry"。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### 若要啟用文字基礎的儲存格中的自動換行  
  
-   將 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.DataGridViewTriState> 列舉值。  下列程式碼範例使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> 屬性來設定整個控制項的換行模式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### 若要指定 DataGridView 儲存格的文字對齊  
  
-   將 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.DataGridViewContentAlignment> 列舉值。  下列程式碼範例使用資料行的 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 屬性，設定特定資料行的對齊。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## 編譯程式碼  
 這些範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，這個控制項包含名為 `UnitPrice`、`ShipDate` 以及 `CustomerName` 的資料行。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 穩固程式設計  
 對於最大延展性，您應該共用使用相同樣式的多個資料列、資料行或儲存格之間的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是為每一個項目分別設定樣式屬性。  如需詳細資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)   
 [如何：自訂 Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)   
 [格式化類型](../../../../docs/standard/base-types/formatting-types.md)