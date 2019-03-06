---
title: HOW TO：篩選檢視中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: 51f95834556153448d416157460cf63da0d409e1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373942"
---
# <a name="how-to-filter-data-in-a-view"></a>HOW TO：篩選檢視中的資料
此範例示範如何篩選檢視中的資料。  
  
## <a name="example"></a>範例  
 若要建立篩選，定義方法，提供篩選邏輯。 做為回呼方法，並接受類型參數的`object`。 下列方法會傳回所有`Order`具有物件`filled`屬性設定為 [否]，篩選出其餘的物件。  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 您接著可以套用篩選器，如下列範例所示。 在此範例中，`myCollectionView`是<xref:System.Windows.Data.ListCollectionView>物件。  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 若要復原篩選，您可以設定<xref:System.Windows.Data.CollectionView.Filter%2A>屬性設`null`:  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 如需有關如何建立或取得檢視的資訊，請參閱 <<c0> [ 取得資料集合的預設檢視](how-to-get-the-default-view-of-a-data-collection.md)。 完整的範例，請參閱[排序及篩選檢視的範例中的項目](https://go.microsoft.com/fwlink/?LinkID=160040)。  
  
 如果您檢視的物件是來自<xref:System.Windows.Data.CollectionViewSource>物件，您設定的事件處理常式來套用篩選邏輯<xref:System.Windows.Data.CollectionViewSource.Filter>事件。 在下列範例中，`listingDataView`的執行個體<xref:System.Windows.Data.CollectionViewSource>。  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 下圖顯示的範例實作`ShowOnlyBargainsFilter`篩選事件處理常式。 這個事件處理常式會使用<xref:System.Windows.Data.FilterEventArgs.Accepted%2A>屬性來篩選掉`AuctionItem`具有物件`CurrentPrice`$25 個或更高。  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [資料繫結概觀](data-binding-overview.md)
- [排序檢視中的資料](how-to-sort-data-in-a-view.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
