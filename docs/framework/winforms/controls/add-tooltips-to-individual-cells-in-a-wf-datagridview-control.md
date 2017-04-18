---
title: "如何：將工具提示加入至 Windows Form DataGridView 控制項中的個別儲存格 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料格, 加入工具提示"
  - "DataGridView 控制項 [Windows Form], 加入工具提示"
  - "工具提示 [Windows Form], 加入到資料格"
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：將工具提示加入至 Windows Form DataGridView 控制項中的個別儲存格
根據預設，工具提示是用來顯示太小而無法顯示出完整內容的 <xref:System.Windows.Forms.DataGridView> 儲存格的值。  不過您可以覆寫這個行為，為個別儲存格設定工具提示值。  這在為使用者顯示儲存格的其他資訊，或提供使用者儲存格內容的替代描述上，是非常有用的。  例如，如果您有顯示狀態圖示的資料列，可能會希望使用工具提供文字說明。  
  
 也可以藉由將 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=fullName> 屬性為 `false`，停用顯示儲存格層級工具提示。  
  
### 若要將工具提示加入至儲存格  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=fullName> 屬性。  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## 編譯程式碼  
  
-   這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，其中包含名為 `Rating` 的資料行，顯示一到四個星號 \("\*"\) 符號的字串值。  控制項的 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件必須與範例中所示的事件處理常式方法相關聯。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 穩固程式設計  
 當您繫結 <xref:System.Windows.Forms.DataGridView> 控制項至外部資料來源，或藉由實作虛擬模式提供自己的資料來源時，您可能會遇到效能問題。  若要避免在使用大量資料時出現效能的負面效應，請處理 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> 事件，而非設定多個儲存格的 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> 屬性。  當您處理這個事件時，取得儲存格 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> 屬性的值會引發事件，並傳回在事件處理常式中所指定的 <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=fullName> 屬性值。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell>   
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)