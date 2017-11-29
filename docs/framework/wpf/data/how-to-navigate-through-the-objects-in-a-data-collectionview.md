---
title: "如何：透過資料 CollectionView 中的物件巡覽"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f20881ed452f1ec78381d17a32b4cc2c77305e0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>如何：透過資料 CollectionView 中的物件巡覽
檢視可讓在不同的方式，根據排序、 篩選或群組中檢視相同的資料集合。 檢視也會提供目前的記錄指標概念，並啟用移動指標。 這個範例示範如何取得目前的物件，以及巡覽資料集合，使用所提供的功能中的物件<xref:System.Windows.Data.CollectionView>類別。  
  
## <a name="example"></a>範例  
 在此範例中，`myCollectionView`是<xref:System.Windows.Data.CollectionView>是對繫結的集合檢視的物件。  
  
 在下列範例中，`OnButton`事件處理常式`Previous`和`Next`按鈕應用程式中，也就是按鈕，好讓使用者巡覽資料集合。 請注意，<xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A>和<xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A>屬性報告是否在目前的記錄指標已有的開始和清單的結尾分別因此的<xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A>和<xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A>可以為適當地呼叫。  
  
 <xref:System.Windows.Data.CollectionView.CurrentItem%2A>檢視的屬性就會轉換為`Order`傳回集合中目前的訂單項目。  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [排序檢視中的資料](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [篩選檢視中的資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [使用 XAML 中的檢視排序和群組資料](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [操作說明主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
