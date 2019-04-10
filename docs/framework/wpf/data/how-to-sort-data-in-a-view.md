---
title: HOW TO：排序檢視中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 32f73d3c3ba213778654f0d1ee7bbae16b9d845b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211253"
---
# <a name="how-to-sort-data-in-a-view"></a>HOW TO：排序檢視中的資料
這個範例說明如何排序檢視中的資料。  
  
## <a name="example"></a>範例  
 下列範例會建立簡易<xref:System.Windows.Controls.ListBox>和<xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click>  按鈕的事件處理常式包含排序項目中的邏輯<xref:System.Windows.Controls.ListBox>以遞減的順序。 您可以新增項目，因為<xref:System.Windows.Controls.ListBox>這種方式將它們加入至<xref:System.Windows.Controls.ItemCollection>的<xref:System.Windows.Controls.ListBox>，以及<xref:System.Windows.Controls.ItemCollection>衍生自<xref:System.Windows.Data.CollectionView>類別。 如果您要繫結您<xref:System.Windows.Controls.ListBox>集合，使用<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性，您可以使用相同的技巧來排序。  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 只要您有檢視物件的參考，您可以使用相同的技巧來排序其他集合檢視的內容。 如需濆爧髍孮檢視的範例，請參閱 <<c0> [ 取得資料集合的預設檢視](how-to-get-the-default-view-of-a-data-collection.md)。 如需其他範例，請參閱[排序 GridView 資料行時按一下標頭](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。 如需有關檢視的詳細資訊，請參閱繫結至集合中[資料繫結概觀](data-binding-overview.md)。  
  
 如需如何將排序邏輯中的範例[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，請參閱 <<c2> [ 排序與群組資料使用 XAML 中的檢視](how-to-sort-and-group-data-using-a-view-in-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [在按一下標頭時排序 GridView 資料行](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [資料繫結概觀](data-binding-overview.md)
- [篩選檢視中的資料](how-to-filter-data-in-a-view.md)
- [HOW TO 主題](data-binding-how-to-topics.md)
