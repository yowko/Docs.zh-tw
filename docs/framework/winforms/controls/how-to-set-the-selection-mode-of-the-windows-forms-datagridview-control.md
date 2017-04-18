---
title: "如何：設定 Windows Form DataGridView 控制項的選取模式 | Microsoft Docs"
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
  - "資料格, 選取模式"
  - "DataGridView 控制項 [Windows Form], 選取模式"
  - "選取範圍, DataGridView 控制項中的模式"
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：設定 Windows Form DataGridView 控制項的選取模式
下列程式碼範例示範如何設定 <xref:System.Windows.Forms.DataGridView> 控制項，使得按一下資料列內的任何位置就會自動選取整個資料列，如此就一次只能選取一個資料列。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>   
 <xref:System.Windows.Forms.DataGridViewSelectionMode>   
 [選取範圍和剪貼簿與 Windows Form DataGridView 控制項搭配使用](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)