---
title: 如何：繫結至集合並根據選取項目顯示資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459153"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>如何：繫結至集合並根據選取項目顯示資訊
在簡單的主要詳細資料案例中，您有一個資料系結 <xref:System.Windows.Controls.ItemsControl>，例如 <xref:System.Windows.Controls.ListBox>。 根據使用者選擇，您會顯示所選取專案的詳細資訊。 這個範例會示範如何執行此案例。  
  
## <a name="example"></a>範例  
 在此範例中，`People` 是 `Person` 類別的 <xref:System.Collections.ObjectModel.ObservableCollection%601>。 此 `Person` 類別包含三個屬性： `FirstName`、`LastName`和 `HomeTown`，所有類型 `string`。  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> 會使用下列定義如何呈現 `Person` 資訊的 <xref:System.Windows.DataTemplate>：  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 以下是此範例所產生之內容的螢幕擷取畫面。 <xref:System.Windows.Controls.ContentControl> 會顯示所選人員的其他屬性。  
  
 ![系結至集合](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 在此範例中要注意的兩件事包括：  
  
1. <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.ContentControl> 系結至相同的來源。 未指定這兩個系結的 <xref:System.Windows.Data.Binding.Path%2A> 屬性，因為這兩個控制項都系結至整個集合物件。  
  
2. 您必須將 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 屬性設定為 `true`，才能讓此作業正常執行。 設定這個屬性可確保選取的專案一律設定為 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。 或者，如果 <xref:System.Windows.Controls.ListBox> 從 <xref:System.Windows.Data.CollectionViewSource>取得資料，則會自動同步處理選取範圍和貨幣。  
  
 請注意，`Person` 類別會以下列方式覆寫 `ToString` 方法。 根據預設，<xref:System.Windows.Controls.ListBox> 會呼叫 `ToString`，並在系結的集合中顯示每個物件的字串表示。 這就是為什麼每個 `Person` 會在 <xref:System.Windows.Controls.ListBox>中顯示為名字。  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>請參閱

- [使用含階層式資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [使用含階層式 XML 資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [資料範本化概觀](data-templating-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
