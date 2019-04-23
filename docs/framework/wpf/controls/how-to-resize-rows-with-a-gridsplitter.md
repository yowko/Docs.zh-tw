---
title: HOW TO：使用 GridSplitter 調整資料列的大小
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: 6760a7a691af4f666294556cae3bc95a4299730a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074270"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>HOW TO：使用 GridSplitter 調整資料列的大小
此範例示範如何使用水平<xref:System.Windows.Controls.GridSplitter>來重新分配的空間中的兩個資料列之間<xref:System.Windows.Controls.Grid>而不需要變更的維度<xref:System.Windows.Controls.Grid>。  
  
## <a name="example"></a>範例  
 **如何建立重疊資料列邊緣的 GridSplitter**  
  
 若要指定<xref:System.Windows.Controls.GridSplitter>，調整大小中的相鄰資料列<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Row%2A>附加屬性設定為其中一個您想要調整大小的資料列。 如果您<xref:System.Windows.Controls.Grid>有一個以上的資料行，設定<xref:System.Windows.Controls.Grid.ColumnSpan%2A>附加屬性指定的資料行數目。 然後設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>要<xref:System.Windows.VerticalAlignment.Top>或<xref:System.Windows.VerticalAlignment.Bottom>（您所設定的對齊方式取決於您想要調整大小之兩個資料列）。 最後，設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性設<xref:System.Windows.HorizontalAlignment.Stretch>。  
  
 下列範例示範如何定義水平<xref:System.Windows.Controls.GridSplitter>，調整大小，相鄰的資料列。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A<xref:System.Windows.Controls.GridSplitter>未佔有自己資料列中的其他控制項可能會被遮蔽<xref:System.Windows.Controls.Grid>。 如需有關如何防止此問題的詳細資訊，請參閱[確保 GridSplitter 是可見的](how-to-make-sure-that-a-gridsplitter-is-visible.md)。  
  
 **如何建立佔有資料列的 GridSplitter**  
  
 若要指定<xref:System.Windows.Controls.GridSplitter>所佔用的資料列<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Row%2A>附加屬性設定為其中一個您想要調整大小的資料列。 如果您<xref:System.Windows.Controls.Grid>有一個以上的資料行，設定<xref:System.Windows.Controls.Grid.ColumnSpan%2A>附加屬性設定為資料行數目。 然後設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>要<xref:System.Windows.VerticalAlignment.Center>，將<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性設<xref:System.Windows.HorizontalAlignment.Stretch>，並設定<xref:System.Windows.Controls.RowDefinition.Height%2A>包含的資料列的<xref:System.Windows.Controls.GridSplitter>至<xref:System.Windows.GridLength.Auto%2A>。  
  
 下列範例示範如何定義水平<xref:System.Windows.Controls.GridSplitter>，佔有一個資料列，並調整大小在左邊或右邊的資料列。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.GridSplitter>
- [HOW-TO 主題](gridsplitter-how-to-topics.md)
