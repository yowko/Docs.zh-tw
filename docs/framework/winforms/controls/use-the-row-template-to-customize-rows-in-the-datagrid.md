---
title: "如何：在 Windows Form DataGridView 控制項中使用資料列範本自訂資料列 | Microsoft Docs"
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
  - "資料格, 自訂資料列"
  - "DataGridView 控制項 [Windows Form], 自訂資料列"
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在 Windows Form DataGridView 控制項中使用資料列範本自訂資料列
<xref:System.Windows.Forms.DataGridView> 控制項使用資料列範本做為加入至控制項的所有資料列的基準，控制項是經由資料繫結 \(Data Binding\)，或當您呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=fullName> 方法而不指定要使用的現有資料列時，加入所有的資料列。  
  
 在資料列的外觀和行為上，資料列範本提供給您的控制，會 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 屬性所提供的更好。  您可使用資料列範本設定任何 <xref:System.Windows.Forms.DataGridViewRow> 屬性，包括 <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>。  
  
 在某些情況下，您必須使用資料列範本以達成特定的效果。  例如，資料列高度資訊無法儲存於 <xref:System.Windows.Forms.DataGridViewCellStyle>，所以您必須使用資料列範本變更所有資料列使用的預設高度。  當您建立衍生自 <xref:System.Windows.Forms.DataGridViewRow> 的類別，且想要在加入新資料列至控制項中時使用自訂型別時，資料列範本也會很有用。  
  
> [!NOTE]
>  只有在加入資料列時才會使用資料列範本。  您無法藉由變更資料列範本來變更現有的資料列。  
  
### 若要使用資料列範本  
  
-   在擷取自 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName> 屬性的物件上設定屬性。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridViewRow>   
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName>   
 [Windows Form DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)