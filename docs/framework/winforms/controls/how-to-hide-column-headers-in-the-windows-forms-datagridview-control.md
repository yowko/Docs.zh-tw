---
title: "如何：隱藏 Windows Form DataGridView 控制項中的資料行行首 | Microsoft Docs"
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
  - "資料行行首, 隱藏"
  - "資料行 [Windows Form], 隱藏資料行行首"
  - "DataGridView 控制項 [Windows Form], 資料行行首"
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：隱藏 Windows Form DataGridView 控制項中的資料行行首
有時候您會想顯示 <xref:System.Windows.Forms.DataGridView>，但不顯示資料行行首。  在 <xref:System.Windows.Forms.DataGridView> 控制項中，<xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> 屬性值會決定是否顯示資料行行首。  
  
### 若要隱藏資料行行首  
  
-   將 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=fullName> 屬性設定為 `false`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)