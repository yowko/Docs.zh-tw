---
title: "如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀 | Microsoft Docs"
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
  - "儲存格, 在 DataGridView 控制項中自訂"
  - "資料格, 自訂儲存格"
  - "DataGridView 控制項 [Windows Form], 自訂儲存格"
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀
您可以藉由管理 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellPainting> 事件，自訂任何儲存格的外觀。  您可以從 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> 的 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> 屬性抽取 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Drawing.Graphics>。  藉由這個 <xref:System.Drawing.Graphics>，您可以影響整個 <xref:System.Windows.Forms.DataGridView> 控制項的外觀，但通常您會只想影響目前正在繪製的儲存格外觀。  <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> 的 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> 屬性能讓您將繪製作業限制為目前正在繪製的儲存格。  
  
 在下列程式碼範例中，將會使用 <xref:System.Windows.Forms.DataGridView> 控制項的色彩配置，在 `ContactName` 資料行中繪製所有儲存格。  每一個儲存格文字內容都會繪製於 <xref:System.Drawing.Color.Crimson%2A>，且會以 <xref:System.Windows.Forms.DataGridView> 控制項之 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性的相同顏色繪製內凹方框。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，且具有 `ContactName` 資料行 \(例如在 Northwind 範例資料庫的 Customers 資料表中的資料行\)。  
  
-   System、System.Windows.Forms 和 System.Drawing 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CellPainting>   
 [自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)