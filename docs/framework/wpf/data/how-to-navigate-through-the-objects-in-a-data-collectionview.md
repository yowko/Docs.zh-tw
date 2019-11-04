---
title: 如何：透過資料 CollectionView 中的物件巡覽
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459701"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>如何：透過資料 CollectionView 中的物件巡覽
Views 可以根據排序、篩選或群組，以不同的方式來查看相同的資料收集。 Views 也提供目前的記錄指標概念，並可讓您移動指標。 這個範例示範如何使用 <xref:System.Windows.Data.CollectionView> 類別中提供的功能，取得目前的物件，以及流覽資料集合中的物件。  
  
## <a name="example"></a>範例  
 在此範例中，`myCollectionView` 是 <xref:System.Windows.Data.CollectionView> 物件，其為系結集合的 view。  
  
 在下列範例中，`OnButton` 是應用程式中 [`Previous`] 和 [`Next`] 按鈕的事件處理常式，這是允許使用者導覽資料收集的按鈕。 請注意，<xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> 和 <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> 屬性會報告目前的記錄指標是否分別來自于清單的開頭和結尾，以便能夠適當地呼叫 <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> 和 <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A>。  
  
 視圖的 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> 屬性會轉換為 `Order`，以傳回集合中目前的訂單專案。  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>請參閱

- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [排序檢視中的資料](how-to-sort-data-in-a-view.md)
- [篩選檢視中的資料](how-to-filter-data-in-a-view.md)
- [使用 XAML 中的檢視排序和群組資料](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [「如何」主題](data-binding-how-to-topics.md)
