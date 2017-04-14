---
title: "如何：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序 | Microsoft Docs"
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
  - "資料行 [Windows Form], 重新排列"
  - "資料格, 重新調整資料行順序"
  - "DataGridView 控制項 [Windows Form], 資料行順序"
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序
當您在 <xref:System.Windows.Forms.DataGridView> 控制項中啟用資料行重新調整順序，使用者可以使用滑鼠拖曳資料行標頭，將資料行移至新的位置。  在 <xref:System.Windows.Forms.DataGridView> 控制項中，<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=fullName> 屬性值會決定使用者是否能將資料行移至不同位置。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[如何：使用設計工具在 Windows Form DataGridView 控制項中啟用資料行重新調整順序](http://msdn.microsoft.com/library/8xwtyc86\(v=vs.110\))。  
  
### 以程式設計方式啟用資料行重新調整順序  
  
-   將 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=fullName> 屬性設定為 `true`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [如何：凍結 Windows Form DataGridView 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)