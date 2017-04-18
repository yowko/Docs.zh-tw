---
title: "如何：將未繫結的資料行加入至已資料繫結的 Windows Form DataGridView 控制項 | Microsoft Docs"
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
  - "資料行 [Windows Form], 未繫結資料"
  - "資料格, 加入未繫結資料行"
  - "DataGridView 控制項 [Windows Form], 未繫結資料"
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：將未繫結的資料行加入至已資料繫結的 Windows Form DataGridView 控制項
您在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示的資料，通常來自於某種的資料來源，但您可能想要顯示不是來自資料來源之資料的資料行。  這種資料行稱為未繫結資料行。  未繫結資料行可以有許多形式。  通常，它們用來提供資料列詳細資料的存取權。  
  
 下列程式碼範例示範如何建立未繫結資料行的 \[詳細資料\] 按鈕以顯示實作主要\/詳細資料案例時﹐與父資料表中的特定資料列相關的子資料表。  若要回應按下按鈕後，實作 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> 事件處理常式，其顯示包含子資料表的表單。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[如何：使用設計工具加入和移除 Windows Form DataGridView 控制項中的資料行](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [在 Windows Form DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)