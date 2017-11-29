---
title: "操作說明：使用 GridSplitter 調整資料列的大小"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6621cc0048270b97c42ff4c4e646b0ddd9ca3477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>操作說明：使用 GridSplitter 調整資料列的大小
這個範例示範如何使用水平<xref:System.Windows.Controls.GridSplitter>轉散發中的兩個資料列之間的空間<xref:System.Windows.Controls.Grid>而不需要變更維度的<xref:System.Windows.Controls.Grid>。  
  
## <a name="example"></a>範例  
 **如何建立重疊資料列邊緣的 GridSplitter**  
  
 若要指定<xref:System.Windows.Controls.GridSplitter>的調整大小，相鄰的資料列中<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Row%2A>附加至您要調整大小的資料列的其中一個屬性。 如果您<xref:System.Windows.Controls.Grid>具有一個以上的資料行設定<xref:System.Windows.Controls.Grid.ColumnSpan%2A>附加屬性，以指定的資料行數目。 然後設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>至<xref:System.Windows.VerticalAlignment.Top>或<xref:System.Windows.VerticalAlignment.Bottom>（您所設定的對齊方式取決於您要調整大小之兩個資料列）。 最後，設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性<xref:System.Windows.HorizontalAlignment.Stretch>。  
  
 下列範例示範如何定義水平<xref:System.Windows.Controls.GridSplitter>的調整大小，相鄰的資料列。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A<xref:System.Windows.Controls.GridSplitter>不會佔用自己的資料列中的其他控制項可能會遮蔽<xref:System.Windows.Controls.Grid>。 如需有關如何防止此問題的詳細資訊，請參閱[確保 GridSplitter 是可見的](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)。  
  
 **如何建立佔有資料列的 GridSplitter**  
  
 若要指定<xref:System.Windows.Controls.GridSplitter>所佔用的資料列中<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Row%2A>附加至您要調整大小的資料列的其中一個屬性。 如果您<xref:System.Windows.Controls.Grid>具有一個以上的資料行設定<xref:System.Windows.Controls.Grid.ColumnSpan%2A>附加屬性的資料行數目。 然後設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>至<xref:System.Windows.VerticalAlignment.Center>，將<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性<xref:System.Windows.HorizontalAlignment.Stretch>，並設定<xref:System.Windows.Controls.RowDefinition.Height%2A>包含的資料列的<xref:System.Windows.Controls.GridSplitter>至<xref:System.Windows.GridLength.Auto%2A>。  
  
 下列範例示範如何定義水平<xref:System.Windows.Controls.GridSplitter>，會佔用一個資料列而調整大小，在左邊或右邊的資料列。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.GridSplitter>  
 [操作說明主題](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
