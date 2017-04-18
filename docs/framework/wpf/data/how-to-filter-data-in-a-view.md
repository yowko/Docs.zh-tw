---
title: "如何：篩選檢視中的資料 | Microsoft Docs"
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
  - "資料繫結, 在檢視中篩選資料"
  - "在檢視中篩選資料"
  - "檢視, 篩選資料"
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：篩選檢視中的資料
這個範例顯示如何篩選檢視中的資料。  
  
## 範例  
 若要建立篩選條件，請定義可提供篩選邏輯的方法。  此方法可做為回呼 \(Callback\)，並接受 `object` 型別的參數。  下列方法會傳回所有將 `filled` 屬性設為 "No" 的 `Order` 物件，而篩選掉其餘物件。  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 接著您可以套用篩選條件，如下列範例所示。  在此範例中，`myCollectionView` 為 <xref:System.Windows.Data.ListCollectionView> 物件。  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 若要復原篩選，您可以將 <xref:System.Windows.Data.CollectionView.Filter%2A> 屬性設為 `null`：  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 如需如何建立或取得檢視的詳細資訊，請參閱 [取得資料集合的預設檢視](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。  如需完整範例，請參閱[在檢視中排序和篩選項目範例](http://go.microsoft.com/fwlink/?LinkID=160040) \(英文\)。  
  
 若您的檢視物件來自 <xref:System.Windows.Data.CollectionViewSource> 物件，您可以藉由設定 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件的事件處理常式來套用篩選邏輯。  在下列範例中，`listingDataView` 為 <xref:System.Windows.Data.CollectionViewSource> 的執行個體。  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 以下顯示 `ShowOnlyBargainsFilter` 篩選事件處理常式範例的實作。  這個事件處理常式使用 <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> 屬性，篩選掉 `CurrentPrice` 為 $25 或以上的 `AuctionItem` 物件。  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## 請參閱  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>   
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [排序檢視中的資料](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)