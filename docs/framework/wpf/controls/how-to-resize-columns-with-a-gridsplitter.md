---
title: "如何：使用 GridSplitter 調整資料行的大小 | Microsoft Docs"
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
  - "方格資料行, 調整大小"
  - "GridSplitter 控制項, 調整方格資料行大小"
  - "調整方格資料行大小"
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用 GridSplitter 調整資料行的大小
本範例說明如何建立垂直 <xref:System.Windows.Controls.GridSplitter>，以重新分配 <xref:System.Windows.Controls.Grid> 中兩行之間的空間，而不變更 <xref:System.Windows.Controls.Grid> 的大小。  
  
## 範例  
 **如何建立重疊在資料行邊緣的 GridSplitter**  
  
 若要指定 <xref:System.Windows.Controls.GridSplitter> 來調整 <xref:System.Windows.Controls.Grid> 中相鄰行的大小，請將 <xref:System.Windows.Controls.Grid.Column%2A> [附加屬性](GTMT)設為要調整大小的其中一個行。  如果 <xref:System.Windows.Controls.Grid> 有多列，請將 <xref:System.Windows.Controls.Grid.RowSpan%2A> 附加屬性設為列數。  接著將 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性設為 <xref:System.Windows.HorizontalAlignment> 或 <xref:System.Windows.HorizontalAlignment> \(設定的對齊方式會根據要調整大小的兩行而定\)。  最後，將 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 屬性設為 <xref:System.Windows.VerticalAlignment>。  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 沒有資料行的 <xref:System.Windows.Controls.GridSplitter> 可能會被 <xref:System.Windows.Controls.Grid> 中的其他控制項所遮蔽。  如需如何避免此問題的詳細資訊，請參閱 [確保 GridSplitter 是可見的](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)。  
  
 **如何建立佔用行空間的 GridSplitter**  
  
 若要指定在 <xref:System.Windows.Controls.Grid> 中佔用行空間的 <xref:System.Windows.Controls.GridSplitter>，請將 <xref:System.Windows.Controls.Grid.Column%2A> [附加屬性](GTMT)設為要調整大小的其中一行。  如果 Grid 有多列，請將 <xref:System.Windows.Controls.Grid.RowSpan%2A> 附加屬性設為列數。  接著將 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 設為 <xref:System.Windows.HorizontalAlignment>、將 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 屬性設為 <xref:System.Windows.VerticalAlignment>，然後將包含 <xref:System.Windows.Controls.GridSplitter> 之行的 <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 設為 <xref:System.Windows.GridLength.Auto%2A>。  
  
 下列範例示範如何定義垂直 <xref:System.Windows.Controls.GridSplitter> 佔用行空間並調整兩側行的大小。  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.GridSplitter>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)