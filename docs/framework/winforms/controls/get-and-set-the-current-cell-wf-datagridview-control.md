---
title: "如何：取得和設定 Windows Form DataGridView 控制項中目前的儲存格 | Microsoft Docs"
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
  - "儲存格, 取得及設定目前的"
  - "DataGridView 控制項 [Windows Form], 取得目前的儲存格"
  - "DataGridView 控制項 [Windows Form], 設定目前的儲存格"
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：取得和設定 Windows Form DataGridView 控制項中目前的儲存格
與 <xref:System.Windows.Forms.DataGridView> 的互動通常需要您以程式設計方式探索目前使用中的是哪個儲存格。  您可能還需要變更目前的儲存格。  您可以使用 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 屬性來執行這些工作。  
  
> [!NOTE]
>  您無法在 <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> 屬性設定為 `false` 的資料列或資料行中設定目前的儲存格。  
  
 變更目前的儲存格也可能會變更選取範圍，依據 <xref:System.Windows.Forms.DataGridView> 控制項的選取模式而定。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)。  
  
### 若要以程式設計方式取得目前的儲存格  
  
-   請使用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### 若要以程式設計方式設定目前的儲存格  
  
-   使用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 屬性。  在下列程式碼範例中，目前的儲存格是設定為資料列 0、資料行 1。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   命名為 `getCurrentCellButton` 和 `setCurrentCellButton` 的 <xref:System.Windows.Forms.Button> 控制項。  在 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 中您必須附加每個按鈕的 <xref:System.Windows.Forms.Control.Click> 事件至範例程式碼中的關聯事件處理常式。  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)