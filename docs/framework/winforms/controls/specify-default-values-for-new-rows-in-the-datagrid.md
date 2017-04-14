---
title: "如何：指定 Windows Form DataGridView 控制項新資料列的預設值 | Microsoft Docs"
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
  - "資料格, 新資料列的預設值"
  - "DataGridView 控制項 [Windows Form], 資料輸入"
  - "DataGridView 控制項 [Windows Form], 新資料列的預設值"
  - "資料列, 指定預設值"
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：指定 Windows Form DataGridView 控制項新資料列的預設值
您可以讓應用程式在新加入的資料列填入預設值，使資料輸入變得更方便。  藉由 <xref:System.Windows.Forms.DataGridView> 類別，您可使用 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件填入預設值。  當使用者輸入新資料錄的資料列時，就會引發此事件。  在程式碼處理這個事件時，您可以將選擇的值填入所要的儲存格。  
  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> 事件來指定新資料列的預設值。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   產生唯一 `CustomerID` 值的 `NewCustomerId` 函式。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的資料輸入](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [使用 Windows Form DataGridView 控制項中用於新增資料錄的資料列](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)