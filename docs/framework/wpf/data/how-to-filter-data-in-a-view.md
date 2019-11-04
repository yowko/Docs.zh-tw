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
ms.openlocfilehash: ea49897ca5e9cb6b639cf7d98ff05bd287c51761
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453478"
---
# <a name="how-to-filter-data-in-a-view"></a>如何：篩選檢視中的資料
這個範例示範如何在視圖中篩選資料。  
  
## <a name="example"></a>範例  
 若要建立篩選準則，請定義提供篩選邏輯的方法。 方法會用來做為回呼，並接受 `object`類型的參數。 下列方法會傳回 `filled` 屬性設定為 "No" 的所有 `Order` 物件，並篩選掉其餘的物件。  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 接著，您可以套用篩選準則，如下列範例所示。 在此範例中，`myCollectionView` 是 <xref:System.Windows.Data.ListCollectionView> 物件。  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 若要復原篩選，您可以將 <xref:System.Windows.Data.CollectionView.Filter%2A> 屬性設定為 `null`：  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 如需如何建立或取得視圖的詳細資訊，請參閱[取得資料集合的預設視圖](how-to-get-the-default-view-of-a-data-collection.md)。 如需完整範例，請參閱[在 View 範例中排序和篩選項目](https://go.microsoft.com/fwlink/?LinkID=160040)。  
  
 如果您的 view 物件來自 <xref:System.Windows.Data.CollectionViewSource> 物件，您可以藉由設定 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件的事件處理常式來套用篩選邏輯。 在下列範例中，`listingDataView` 是 <xref:System.Windows.Data.CollectionViewSource>的實例。  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 以下顯示範例的執行 `ShowOnlyBargainsFilter` filter 事件處理常式。 這個事件處理常式會使用 <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> 屬性，篩選出 `CurrentPrice` 為 $25 或更高的 `AuctionItem` 物件。  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [排序檢視中的資料](how-to-sort-data-in-a-view.md)
- [「如何」主題](data-binding-how-to-topics.md)
