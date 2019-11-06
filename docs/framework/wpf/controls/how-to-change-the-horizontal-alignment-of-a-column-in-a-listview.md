---
title: 如何：變更 ListView 中資料行的水平對齊
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 5447f1a73b008b2ed4f345eba00f4d631e11e257
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458600"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>如何：變更 ListView 中資料行的水平對齊
根據預設，<xref:System.Windows.Controls.ListViewItem> 中每個資料行的內容都會靠左對齊。 您可以藉由提供 <xref:System.Windows.DataTemplate> 並在 <xref:System.Windows.DataTemplate>內的專案上設定 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性，來變更每個資料行的對齊方式。 本主題說明 <xref:System.Windows.Controls.ListView> 預設如何對齊其內容，以及如何變更 <xref:System.Windows.Controls.ListView>中某個資料行的對齊方式。  
  
## <a name="example"></a>範例  
 在下列範例中，[`Title`] 和 [`ISBN`] 資料行中的資料是靠左對齊。  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 若要變更 `ISBN` 資料行的對齊，您必須指定每個 <xref:System.Windows.Controls.ListViewItem> 的 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 屬性 <xref:System.Windows.HorizontalAlignment.Stretch>，以便每個 <xref:System.Windows.Controls.ListViewItem> 中的專案可以橫跨或定位於每個資料行的整個寬度。 因為 <xref:System.Windows.Controls.ListView> 系結至資料來源，所以您必須建立設定 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>的樣式。 接下來，您必須使用 <xref:System.Windows.DataTemplate> 來顯示內容，而不是使用 [<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>] 屬性。 若要顯示每個範本的 `ISBN`，<xref:System.Windows.DataTemplate> 只可以包含將其 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性設定為 <xref:System.Windows.HorizontalAlignment.Right>的 <xref:System.Windows.Controls.TextBlock>。  
  
 下列範例會定義使 `ISBN` 資料行靠右對齊所需的樣式和 <xref:System.Windows.DataTemplate>，並將 <xref:System.Windows.Controls.GridViewColumn> 變更為參考 <xref:System.Windows.DataTemplate>。  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>請參閱

- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [資料範本化概觀](../data/data-templating-overview.md)
- [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView 概觀](listview-overview.md)
