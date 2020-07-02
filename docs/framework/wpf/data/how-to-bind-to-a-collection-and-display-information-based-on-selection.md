---
title: 如何：繫結至集合並根據選取項目顯示資訊
description: 請遵循此範例來瞭解如何系結至集合，並根據 Windows Presentation Foundation （WPF）中的選取範圍來顯示資訊。
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619607"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>如何：繫結至集合並根據選取項目顯示資訊
在簡單的主版詳細案例中，您有資料系結， <xref:System.Windows.Controls.ItemsControl> 例如 <xref:System.Windows.Controls.ListBox> 。 根據使用者選擇，您會顯示所選取專案的詳細資訊。 這個範例會示範如何執行此案例。  
  
## <a name="example"></a>範例  
 在此範例中， `People` 是 <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` 類別的。 這個 `Person` 類別包含三個屬性： `FirstName` 、 `LastName` 和 `HomeTown` ，全都是型別 `string` 。  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl>會使用下列 <xref:System.Windows.DataTemplate> 定義呈現資訊的方式 `Person` ：  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 以下是此範例所產生之內容的螢幕擷取畫面。 會 <xref:System.Windows.Controls.ContentControl> 顯示所選人員的其他屬性。  
  
 ![繫結至集合](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 在此範例中要注意的兩件事包括：  
  
1. <xref:System.Windows.Controls.ListBox>和系結 <xref:System.Windows.Controls.ContentControl> 至相同的來源。 <xref:System.Windows.Data.Binding.Path%2A>未指定這兩個系結的屬性，因為這兩個控制項都系結至整個集合物件。  
  
2. 您必須將屬性設定為，才能 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> `true` 讓此作業正常執行。 設定這個屬性可確保選取的專案一律設定為 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> 。 或者，如果 <xref:System.Windows.Controls.ListBox> 從取得資料 <xref:System.Windows.Data.CollectionViewSource> ，它會自動同步處理選取範圍和貨幣。  
  
 請注意， `Person` 類別會以 `ToString` 下列方式覆寫方法。 根據預設，會 <xref:System.Windows.Controls.ListBox> 呼叫 `ToString` 並顯示系結集合中每個物件的字串表示。 這就是為什麼每個 `Person` 都會顯示為中的名字 <xref:System.Windows.Controls.ListBox> 。  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>另請參閱

- [搭配階層式資料使用主版-詳細模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [搭配階層式 XML 資料使用主版-詳細模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [資料範本化概觀](data-templating-overview.md)
- [操作說明主題](data-binding-how-to-topics.md)
