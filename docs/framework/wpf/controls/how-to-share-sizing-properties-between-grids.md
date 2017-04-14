---
title: "如何：在格線之間共用調整大小屬性 | Microsoft Docs"
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
  - "Grid 控制項, 共用資料行的調整大小資料"
  - "Grid 控制項, 共用資料列的調整大小資料"
  - "Grid 控制項中的調整大小資料"
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：在格線之間共用調整大小屬性
本範例說明如何共用 <xref:System.Windows.Controls.Grid> 項目之間的資料行和資料列調整大小資料，以維持調整大小的一致性。  
  
## 範例  
 下列範例使用兩個 <xref:System.Windows.Controls.Grid> 項目，做為父代 <xref:System.Windows.Controls.DockPanel> 的子項目。  <xref:System.Windows.Controls.Grid> 的 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> [附加屬性](GTMT)定義於父代 <xref:System.Windows.Controls.DockPanel>。  
  
 此範例使用兩個 <xref:System.Windows.Controls.Button> 項目以控制屬性值，每個項目代表一個布林屬性值。  當 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> 屬性值設定為 `true` 時，<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> 的每一資料行或資料列的成員，不論資料列或資料行的內容為何，都會共用調整大小資訊。  
  
 [!code-xml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 下列程式碼後置範例處理按鈕 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件所引發的方法。  此範例將這些方法呼叫的結果寫至 <xref:System.Windows.Controls.TextBlock> 項目，此項目使用相關的 Get 方法將新的屬性值輸出為字串。  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)