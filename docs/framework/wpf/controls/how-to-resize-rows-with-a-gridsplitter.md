---
title: "如何：使用 GridSplitter 調整資料列的大小 | Microsoft Docs"
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
  - "方格資料列, 調整大小"
  - "GridSplitter 控制項, 調整方格資料列大小"
  - "調整方格資料列大小"
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用 GridSplitter 調整資料列的大小
本範例示範如何使用水平 <xref:System.Windows.Controls.GridSplitter> 重新分配 <xref:System.Windows.Controls.Grid> 中兩列之間的空間，而不變更 <xref:System.Windows.Controls.Grid> 的大小。  
  
## 範例  
 **如何建立重疊在資料列邊緣的 GridSplitter**  
  
 若要指定 <xref:System.Windows.Controls.GridSplitter> 來調整 <xref:System.Windows.Controls.Grid> 中相鄰列的大小，請將 <xref:System.Windows.Controls.Grid.Row%2A> [附加屬性](GTMT)設為要調整大小的其中一列。  如果 <xref:System.Windows.Controls.Grid> 有多欄，請設定 <xref:System.Windows.Controls.Grid.ColumnSpan%2A> 附加屬性來指定欄數。  接著將 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 設為 <xref:System.Windows.VerticalAlignment> 或 <xref:System.Windows.VerticalAlignment> \(設定的對齊方式會根據要調整大小的兩列而定\)。  最後，將 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性設為 <xref:System.Windows.HorizontalAlignment>。  
  
 下列範例示範如何定義調整相鄰列大小的水平 <xref:System.Windows.Controls.GridSplitter>。  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 不佔列空間的 <xref:System.Windows.Controls.GridSplitter> 可能會被 <xref:System.Windows.Controls.Grid> 中的其他控制項所遮蔽。  如需如何避免此問題的詳細資訊，請參閱 [確保 GridSplitter 是可見的](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)。  
  
 **如何建立佔用列空間的 GridSplitter**  
  
 若要指定在 <xref:System.Windows.Controls.Grid> 中佔用一列的 <xref:System.Windows.Controls.GridSplitter>，請將 <xref:System.Windows.Controls.Grid.Row%2A> [附加屬性](GTMT)設為要調整大小的其中一列。  如果 <xref:System.Windows.Controls.Grid> 有多欄，請將 <xref:System.Windows.Controls.Grid.ColumnSpan%2A> 附加屬性設為欄數。  接著將 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 設為 <xref:System.Windows.VerticalAlignment>、將 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性設為 <xref:System.Windows.HorizontalAlignment>，然後將包含 <xref:System.Windows.Controls.GridSplitter> 之列的 <xref:System.Windows.Controls.RowDefinition.Height%2A> 設為 <xref:System.Windows.GridLength.Auto%2A>。  
  
 下列範例示範如何定義水平 <xref:System.Windows.Controls.GridSplitter>，佔用列空間並調整列兩側的大小。  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.GridSplitter>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)