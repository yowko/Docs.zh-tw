---
title: "如何：防止在 Windows Form DataGridView 控制項中新增和刪除資料列 | Microsoft Docs"
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
  - "資料輸入, 在方格中停用"
  - "資料格, 停用資料輸入"
  - "DataGridView 控制項 [Windows Form], 停用資料輸入"
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：防止在 Windows Form DataGridView 控制項中新增和刪除資料列
有時候您會想要防止使用者在您的 <xref:System.Windows.Forms.DataGridView> 控制項中輸入新的資料列或刪除現有的資料列。   <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性會指出新記錄的資料列是否出現在控制項的底部，而 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> 屬性會指出是否可以移除資料列。  下列程式碼範例會使用這些屬性，也將會設定 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> 屬性使控制項為完全唯讀。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[如何：在使用設計工具的 Windows Form DataGridView 控制項中避免資料列新增與刪除](http://msdn.microsoft.com/library/k5c88sw3%20\(v=vs.110\))。  
  
## 範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)