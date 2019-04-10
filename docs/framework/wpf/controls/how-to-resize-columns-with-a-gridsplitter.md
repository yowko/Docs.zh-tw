---
title: HOW TO：使用 GridSplitter 調整資料行的大小
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: f743e9ccf8a984a646a4b8f05ee99162e5bc73ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210434"
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>HOW TO：使用 GridSplitter 調整資料行的大小
此範例示範如何建立垂直<xref:System.Windows.Controls.GridSplitter>來重新分配的空間中的兩個資料行之間<xref:System.Windows.Controls.Grid>而不需要變更的維度<xref:System.Windows.Controls.Grid>。  
  
## <a name="example"></a>範例  
 **如何建立 GridSplitter 重疊的資料行的邊緣**  
  
 若要指定<xref:System.Windows.Controls.GridSplitter>，調整大小，在相鄰的資料行<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Column%2A>附加屬性設定為其中一個您想要調整大小的資料行。 如果您<xref:System.Windows.Controls.Grid>有一個以上的資料列，設定<xref:System.Windows.Controls.Grid.RowSpan%2A>附加屬性的資料列數目。 然後設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性，以<xref:System.Windows.HorizontalAlignment.Left>或<xref:System.Windows.HorizontalAlignment.Right>（您所設定的對齊方式取決於您想要調整大小的兩個資料行上）。 最後，設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性設<xref:System.Windows.VerticalAlignment.Stretch>。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A<xref:System.Windows.Controls.GridSplitter>沒有自己的資料行中的其他控制項可能會被遮蔽<xref:System.Windows.Controls.Grid>。 如需有關如何防止此問題的詳細資訊，請參閱[確保 GridSplitter 是可見的](how-to-make-sure-that-a-gridsplitter-is-visible.md)。  
  
 **如何建立佔有資料行的 GridSplitter**  
  
 若要指定<xref:System.Windows.Controls.GridSplitter>所佔用的資料行<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Column%2A>附加屬性設定為其中一個您想要調整大小的資料行。 如果您的網格有多個資料列，設定<xref:System.Windows.Controls.Grid.RowSpan%2A>附加屬性的資料列數目。 然後設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>要<xref:System.Windows.HorizontalAlignment.Center>，將<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性設<xref:System.Windows.VerticalAlignment.Stretch>，並設定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>包含的資料行的<xref:System.Windows.Controls.GridSplitter>至<xref:System.Windows.GridLength.Auto%2A>。  
  
 下列範例示範如何定義垂直<xref:System.Windows.Controls.GridSplitter>，佔有一個資料行，並調整大小在左邊或右邊的資料行。  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.GridSplitter>
- [HOW TO 主題](gridsplitter-how-to-topics.md)
