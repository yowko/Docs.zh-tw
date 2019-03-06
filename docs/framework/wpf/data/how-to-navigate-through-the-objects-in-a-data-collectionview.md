---
title: HOW TO：透過資料 CollectionView 中的物件巡覽
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 9272a2f635a62abdac2746f2c8cce515812706f6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355775"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>HOW TO：透過資料 CollectionView 中的物件巡覽
檢視可讓在不同的方式，取決於排序、 篩選或群組中檢視相同的資料收集。 檢視也會提供目前記錄指標的概念，並啟用移動指標。 此範例示範如何取得目前的物件，以及透過使用中提供的功能資料集合中的物件巡覽<xref:System.Windows.Data.CollectionView>類別。  
  
## <a name="example"></a>範例  
 在此範例中，`myCollectionView`是<xref:System.Windows.Data.CollectionView>對繫結的集合是一種檢視的物件。  
  
 在下列範例中，`OnButton`事件處理常式`Previous`和`Next`按鈕在應用程式，也就是按鈕，可讓使用者導覽資料收集。 請注意，<xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A>並<xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A>屬性會報告是否目前記錄指標已有的開始和清單的結尾分別因此，<xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A>和<xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A>可以為適當地呼叫。  
  
 <xref:System.Windows.Data.CollectionView.CurrentItem%2A>檢視的屬性，這會轉換為`Order`返回目前的訂單項目集合中。  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>另請參閱
- [資料繫結概觀](data-binding-overview.md)
- [排序檢視中的資料](how-to-sort-data-in-a-view.md)
- [篩選檢視中的資料](how-to-filter-data-in-a-view.md)
- [使用 XAML 中的檢視排序和群組資料](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
