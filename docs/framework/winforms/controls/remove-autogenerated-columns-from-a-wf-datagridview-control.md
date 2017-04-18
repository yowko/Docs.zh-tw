---
title: "如何：移除 Windows Form DataGridView 控制項中自動產生的資料行 | Microsoft Docs"
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
  - "資料行 [Windows Form], 移除"
  - "DataGridView 控制項 [Windows Form], 移除資料行"
ms.assetid: 92e28d98-95a3-446c-9150-41b7c7e5be15
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：移除 Windows Form DataGridView 控制項中自動產生的資料行
當 <xref:System.Windows.Forms.DataGridView> 控制項是設定成根據資料來源的資料自動產生資料行時，可以選擇性地省略某些資料行。  您可以藉由呼叫 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合上的 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> 方法來這麼做。  或者，也可以透過將 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 屬性設定為 `false`，從檢視隱藏資料行。  如果想在某些情況下顯示隱藏的資料行，或者需要存取資料行中的資料但不顯示資料，這個技巧會很有用。  
  
### 若要移除自動產生的資料行  
  
-   呼叫 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合上的 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#111)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#111)]  
  
### 若要隱藏自動產生的資料行  
  
-   將資料行的 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 屬性設定為 `false`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#112)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#112)]  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#110)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#110)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項繫結至包含有 `Fax` 和 `CustomerID` 資料行的資料表，例如 Northwind 範例資料庫中的 `Customers` 資料表。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)