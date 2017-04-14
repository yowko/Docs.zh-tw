---
title: "如何：透過資料 CollectionView 中的物件巡覽 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CollectionView, 巡覽物件"
  - "資料繫結, 在資料 CollectionView 中巡覽物件"
  - "在資料 CollectionView 中巡覽物件"
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：透過資料 CollectionView 中的物件巡覽
根據排序、篩選或群組而定，可以透過檢視，以不同的方式檢視相同的資料集合。  檢視也提供目前記錄指標的概念，也可以移動指標。  這個範例顯示如何使用 <xref:System.Windows.Data.CollectionView> 類別所提供的功能，取得目前物件以及巡覽資料集合中的所有物件。  
  
## 範例  
 在此範例中，`myCollectionView` 是 <xref:System.Windows.Data.CollectionView> 物件，該物件為繫結集合的檢視。  
  
 在下面的範例中，`OnButton` 為應用程式中 `Previous` 和 `Next` 按鈕的事件處理常式，這些按鈕可供使用者巡覽資料集合。  請注意，<xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> 和 <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> 屬性會報告目前的記錄指標是否已分別來到清單的開頭和結尾，以便適當地呼叫 <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> 和 <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A>。  
  
 檢視的 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> 屬性會轉型為 `Order`，以傳回集合中目前的順序項目。  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [排序檢視中的資料](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [篩選檢視中的資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [使用 XAML 排序和分組資料](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)