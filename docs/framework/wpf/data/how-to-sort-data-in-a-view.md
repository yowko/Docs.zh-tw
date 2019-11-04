---
title: 如何：排序檢視中的資料
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
ms.openlocfilehash: 14314ed019f9194a657787bd767ae68615e94ac7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454835"
---
# <a name="how-to-sort-data-in-a-view"></a>如何：排序檢視中的資料
此範例說明如何在視圖中排序資料。  
  
## <a name="example"></a>範例  
 下列範例會建立簡單的 <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.Button>：  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式包含以遞減順序排序 <xref:System.Windows.Controls.ListBox> 中專案的邏輯。 您可以這樣做，因為將專案新增至 <xref:System.Windows.Controls.ListBox> 這種方式會將它們新增至 <xref:System.Windows.Controls.ListBox>的 <xref:System.Windows.Controls.ItemCollection>，而 <xref:System.Windows.Controls.ItemCollection> 衍生自 <xref:System.Windows.Data.CollectionView> 類別。 如果您使用 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性將 <xref:System.Windows.Controls.ListBox> 系結至集合，則可以使用相同的技巧進行排序。  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 只要您擁有 view 物件的參考，就可以使用相同的技巧來排序其他集合視圖的內容。 如需如何取得視圖的範例，請參閱[取得資料集合的預設視圖](how-to-get-the-default-view-of-a-data-collection.md)。 如需其他範例，請參閱[在按一下標頭時排序 GridView 資料行](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。 如需有關 views 的詳細資訊，請參閱系結至資料系結中的集合[總覽](../../../desktop-wpf/data/data-binding-overview.md)。  
  
 如需如何在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中套用排序邏輯的範例，請參閱[使用 XAML 中的視圖排序和分組資料](how-to-sort-and-group-data-using-a-view-in-xaml.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [在按一下標頭時排序 GridView 資料行](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [篩選檢視中的資料](how-to-filter-data-in-a-view.md)
- [「如何」主題](data-binding-how-to-topics.md)
