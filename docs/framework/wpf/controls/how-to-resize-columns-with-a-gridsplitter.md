---
title: "操作說明：使用 GridSplitter 調整資料行的大小"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d68d829e5543b1c299668493c11b62ccb11d81af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>操作說明：使用 GridSplitter 調整資料行的大小
這個範例示範如何建立垂直<xref:System.Windows.Controls.GridSplitter>才能重新發佈中的兩個資料行之間的間距<xref:System.Windows.Controls.Grid>而不需要變更維度的<xref:System.Windows.Controls.Grid>。  
  
## <a name="example"></a>範例  
 **如何建立重疊資料行邊緣的 GridSplitter**  
  
 若要指定<xref:System.Windows.Controls.GridSplitter>的調整大小，相鄰的資料行中<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Column%2A>附加至其中一個您要調整大小的資料行的屬性。 如果您<xref:System.Windows.Controls.Grid>有一個以上的資料列集<xref:System.Windows.Controls.Grid.RowSpan%2A>附加屬性的資料列數目。 然後設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性<xref:System.Windows.HorizontalAlignment.Left>或<xref:System.Windows.HorizontalAlignment.Right>（您所設定的對齊方式取決於您要調整大小的兩個資料行上）。 最後，設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性<xref:System.Windows.VerticalAlignment.Stretch>。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A<xref:System.Windows.Controls.GridSplitter>沒有自己的資料行中的其他控制項可能會遮蔽<xref:System.Windows.Controls.Grid>。 如需有關如何防止此問題的詳細資訊，請參閱[確保 GridSplitter 是可見的](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)。  
  
 **如何建立佔有資料行的 GridSplitter**  
  
 若要指定<xref:System.Windows.Controls.GridSplitter>，佔用中的資料行<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Column%2A>附加至其中一個您要調整大小的資料行的屬性。 如果方格具有多個資料列，設定<xref:System.Windows.Controls.Grid.RowSpan%2A>附加屬性的資料列數目。 然後設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>至<xref:System.Windows.HorizontalAlignment.Center>，將<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性<xref:System.Windows.VerticalAlignment.Stretch>，並設定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>包含的資料行的<xref:System.Windows.Controls.GridSplitter>至<xref:System.Windows.GridLength.Auto%2A>。  
  
 下列範例示範如何定義垂直<xref:System.Windows.Controls.GridSplitter>佔用資料行，而且會在左邊或右邊的資料行的調整大小。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.GridSplitter>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
