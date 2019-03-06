---
title: HOW TO：繫結至集合並根據選取項目顯示資訊
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
ms.openlocfilehash: 5ceda723ad982fc788e8d0b81e6cf92975790682
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360390"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>HOW TO：繫結至集合並根據選取項目顯示資訊
在簡單的主版詳細資料案例中，您會有資料繫結<xref:System.Windows.Controls.ItemsControl>這類<xref:System.Windows.Controls.ListBox>。 您根據使用者選取項目，顯示有關所選項目的詳細資訊。 此範例示範如何實作此案例。  
  
## <a name="example"></a>範例  
 在此範例中，`People`已<xref:System.Collections.ObjectModel.ObservableCollection%601>的`Person`類別。 這`Person`類別包含三個屬性： `FirstName`， `LastName`，以及`HomeTown`，所有型別的`string`。  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl>會使用下列<xref:System.Windows.DataTemplate>的定義方式的資訊`Person`呈現：  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 以下是範例所產生的螢幕擷取畫面。 <xref:System.Windows.Controls.ContentControl>顯示選取之人員的其他屬性。  
  
 ![繫結至集合](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 請注意，在此範例中的兩個事項如下：  
  
1.  <xref:System.Windows.Controls.ListBox>而<xref:System.Windows.Controls.ContentControl>繫結至相同的來源。 <xref:System.Windows.Data.Binding.Path%2A>因為兩個控制項都繫結至整個集合物件未指定這兩個繫結的屬性。  
  
2.  您必須設定<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>屬性設`true`才能運作。 設定這個屬性可確保已選取的項目一律會設為<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。 或者，如果<xref:System.Windows.Controls.ListBox>取得其資料從<xref:System.Windows.Data.CollectionViewSource>，自動同步選取項目和貨幣。  
  
 請注意，`Person`類別會覆寫`ToString`方法以下列方式。 根據預設，<xref:System.Windows.Controls.ListBox>呼叫`ToString`和顯示繫結集合中的每個物件的字串表示。 這就是為什麼每個`Person`會顯示中的第一個名稱為<xref:System.Windows.Controls.ListBox>。  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>另請參閱
- [使用含階層式資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [使用含階層式 XML 資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [資料繫結概觀](data-binding-overview.md)
- [資料範本化概觀](data-templating-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
