---
title: "如何：使用 Grid 建置標準 UI 對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "對話方塊, 建立"
  - "Grid 控制項, 建立, 對話方塊"
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用 Grid 建置標準 UI 對話方塊
這個範例說明如何使用 <xref:System.Windows.Controls.Grid> 項目，建立標準的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 對話方塊。  
  
## 範例  
 下列範例會建立一個對話方塊，就像 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 作業系統中的 \[**執行**\] 對話方塊一樣。  
  
 這個範例會建立一個 <xref:System.Windows.Controls.Grid> 並使用 <xref:System.Windows.Controls.ColumnDefinition> 和 <xref:System.Windows.Controls.RowDefinition> 類別，以定義五個資料行和四個資料列。  
  
 然後範例會再新增並放置一個 <xref:System.Windows.Controls.Image> \(`RunIcon.png`\)，以代表對話方塊中找到的影像。  影像會放在<xref:System.Windows.Controls.Grid> 的第一資料行和資料列中 \(左上角\)。  
  
 接下來，範例會新增一個 <xref:System.Windows.Controls.TextBlock> 項目至第一個資料行，並且會跨越到第一個資料列下的所有資料行。  然後再增加一個 <xref:System.Windows.Controls.TextBlock> 項目至第一個資料行的第二個資料列，以代表 \[**開啟**\] 文字方塊。  接著是 <xref:System.Windows.Controls.TextBlock>，代表資料輸入區。  
  
 最後，範例會新增三個 <xref:System.Windows.Controls.Button> 項目到最後一個資料列，這三個項目分別代表 \[**確定**\]、\[**取消**\] 和 \[**瀏覽**\] 事件。  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.GridUnitType>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)