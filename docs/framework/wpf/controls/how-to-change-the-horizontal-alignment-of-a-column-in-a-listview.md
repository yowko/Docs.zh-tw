---
title: HOW TO：變更 ListView 中資料行的水平對齊
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 528a711c1cf7992bb32c0aa4d6e81d71744c9f80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102657"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>HOW TO：變更 ListView 中資料行的水平對齊
根據預設，每個資料行的內容<xref:System.Windows.Controls.ListViewItem>靠左對齊。 您可以藉由提供變更的每個資料行對齊<xref:System.Windows.DataTemplate>並設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>內的項目上的屬性<xref:System.Windows.DataTemplate>。 本主題說明如何<xref:System.Windows.Controls.ListView>其內容的預設值，以及如何變更一個資料行中的對齊方式對齊<xref:System.Windows.Controls.ListView>。  
  
## <a name="example"></a>範例  
 在下列範例中中的資料`Title`和`ISBN`資料行是靠左對齊。  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 若要變更的對齊方式`ISBN` 欄中，您需要指定<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>每個屬性<xref:System.Windows.Controls.ListViewItem>是<xref:System.Windows.HorizontalAlignment.Stretch>，以便在每個項目<xref:System.Windows.Controls.ListViewItem>可以跨越或定位沿著每個資料行的整個寬度。 因為<xref:System.Windows.Controls.ListView>繫結至資料來源，您需要建立一個樣式，設定<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>。 接下來，您必須使用<xref:System.Windows.DataTemplate>若要顯示的內容，而不是使用<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性。 若要顯示`ISBN`的每個範本中，<xref:System.Windows.DataTemplate>可以只包含<xref:System.Windows.Controls.TextBlock>具有其<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性設定為<xref:System.Windows.HorizontalAlignment.Right>。  
  
 下列範例定義的樣式並<xref:System.Windows.DataTemplate>需要製作`ISBN`靠右對齊的資料行並變更<xref:System.Windows.Controls.GridViewColumn>參考<xref:System.Windows.DataTemplate>。  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>另請參閱

- [資料繫結概觀](../data/data-binding-overview.md)
- [資料範本化概觀](../data/data-templating-overview.md)
- [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView 概觀](listview-overview.md)
