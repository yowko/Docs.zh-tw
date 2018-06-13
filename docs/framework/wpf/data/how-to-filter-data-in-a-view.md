---
title: 如何：篩選檢視中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: 55ec68e8918c9f7fbc9d3ac0062926cc03cb5e10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556649"
---
# <a name="how-to-filter-data-in-a-view"></a>如何：篩選檢視中的資料
這個範例示範如何篩選檢視中的資料。  
  
## <a name="example"></a>範例  
 若要建立篩選，定義提供篩選的邏輯的方法。 做為回呼方法，並接受類型的參數`object`。 下列方法會傳回所有`Order`物件與`filled`屬性設定為 [否]，篩選出其餘的物件。  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 然後，如下列範例所示，您可以套用篩選器。 在此範例中，`myCollectionView`是<xref:System.Windows.Data.ListCollectionView>物件。  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 若要復原篩選，您可以設定<xref:System.Windows.Data.CollectionView.Filter%2A>屬性`null`:  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 如需如何建立或取得的檢視資訊，請參閱[取得預設的檢視資料收集](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。 完整的範例，請參閱[排序及篩選檢視範例中的項目](http://go.microsoft.com/fwlink/?LinkID=160040)。  
  
 如果您檢視物件來自於<xref:System.Windows.Data.CollectionViewSource>物件，您設定的事件處理常式來套用篩選邏輯<xref:System.Windows.Data.CollectionViewSource.Filter>事件。 在下列範例中，`listingDataView`的執行個體<xref:System.Windows.Data.CollectionViewSource>。  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 下列範例示範實作範例`ShowOnlyBargainsFilter`篩選事件處理常式。 此事件處理常式使用<xref:System.Windows.Data.FilterEventArgs.Accepted%2A>屬性來篩選掉`AuctionItem`物件`CurrentPrice`為 $25 或更高。  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [排序檢視中的資料](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
