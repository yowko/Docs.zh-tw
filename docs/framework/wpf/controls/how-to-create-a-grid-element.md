---
title: "如何：建立 Grid 項目 | Microsoft Docs"
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
  - "Grid 控制項, 建立, 方格執行個體"
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：建立 Grid 項目
## 範例  
 下列範例說明如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 或程式碼，以建立及使用 <xref:System.Windows.Controls.Grid> 的執行個體。  這個範例使用三個 <xref:System.Windows.Controls.ColumnDefinition> 物件以及三個 <xref:System.Windows.Controls.RowDefinition> 物件建立共有九個儲存格、像工作表的格線。  每個儲存格內含一個代表資料的 <xref:System.Windows.Controls.TextBlock> 項目，頂端列內含套用了 <xref:System.Windows.Controls.Grid.ColumnSpan%2A> 屬性的 <xref:System.Windows.Controls.TextBlock>。  <xref:System.Windows.Controls.Grid.ShowGridLines%2A> 屬性已啟用，以顯示每一個儲存格的邊界。  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Grid>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)