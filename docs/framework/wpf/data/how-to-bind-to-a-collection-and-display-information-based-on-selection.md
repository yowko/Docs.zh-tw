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
ms.openlocfilehash: 154f4b9b6024d064e73d64c44e2398a5da47052c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>如何：繫結至集合並根據選取項目顯示資訊
在簡單的主版詳細資料案例中，您必須要有資料繫結<xref:System.Windows.Controls.ItemsControl>例如<xref:System.Windows.Controls.ListBox>。 您根據使用者選取項目，顯示有關所選項目的詳細資訊。 這個範例示範如何實作此案例。  
  
## <a name="example"></a>範例  
 在此範例中，`People`是<xref:System.Collections.ObjectModel.ObservableCollection%601>的`Person`類別。 這`Person`類別包含三個屬性： `FirstName`， `LastName`，和`HomeTown`，所有的型別`string`。  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl>會使用下列<xref:System.Windows.DataTemplate>，定義方式的資訊`Person`呈現：  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 以下是這個範例會產生的螢幕擷取畫面。 <xref:System.Windows.Controls.ContentControl>顯示選取之人員的其他屬性。  
  
 ![繫結至集合](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 請注意，在此範例中的兩個事項如下：  
  
1.  <xref:System.Windows.Controls.ListBox>和<xref:System.Windows.Controls.ContentControl>繫結至相同的來源。 <xref:System.Windows.Data.Binding.Path%2A>由於兩個控制項要繫結至整個集合物件未指定這兩個繫結的屬性。  
  
2.  您必須設定<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>屬性`true`，才能順利運作。 設定這個屬性可確保已選取的項目一律會設為<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。 或者，如果<xref:System.Windows.Controls.ListBox>取得它的資料<xref:System.Windows.Data.CollectionViewSource>，自動同步選取範圍和貨幣。  
  
 請注意，`Person`類別覆寫`ToString`方法以下列方式。 根據預設，<xref:System.Windows.Controls.ListBox>呼叫`ToString`並顯示每個物件的字串表示，此繫結集合中。 這就是為什麼每個`Person`顯示中的第一個名稱為<xref:System.Windows.Controls.ListBox>。  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>另請參閱  
 [使用含階層式資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [使用含階層式 XML 資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
