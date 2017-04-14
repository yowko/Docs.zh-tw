---
title: "如何：取得資料集合的預設檢視 | Microsoft Docs"
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
  - "建立, 資料集合的檢視"
  - "資料繫結, 建立資料集合的檢視"
  - "資料集合, 建立檢視"
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：取得資料集合的預設檢視
根據排序、篩選或群組準則而定，可以透過檢視，以不同的方式檢視相同的資料集合。  每個集合都有一個共用的預設檢視，這會在繫結指定集合做為來源時，當做實際繫結來源使用。  本範例示範如何取得集合的預設檢視。  
  
## 範例  
 若要建立檢視，您需要集合的物件參考。  若要取得這個資料物件，可以參考您自己的程式碼後置 \(Code\-Behind\) 物件、取得資料內容、取得資料來源的屬性 \(Property\)，或取得繫結的屬性 \(Property\)。  這個範例示範如何取得資料物件的 <xref:System.Windows.FrameworkElement.DataContext%2A>，並用它來直接取得這個集合的預設集合檢視。  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 在這個範例中，根項目是 <xref:System.Windows.Controls.StackPanel>。  <xref:System.Windows.FrameworkElement.DataContext%2A> 設為 *myDataSource*，它參考的資料提供者是 *Order* 物件的 <xref:System.Collections.ObjectModel.ObservableCollection%601>。  
  
 [!code-xml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 或者，您也可以使用 <xref:System.Windows.Data.CollectionViewSource> 類別具現化並繫結至您自己的集合。  此集合檢視僅供直接與它繫結的控制項共用。  如需範例，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)的＜如何建立檢視＞一節。  
  
 如需集合檢視提供的功能範例，請參閱 [排序檢視中的資料](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)、[篩選檢視中的資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md) 和 [透過資料 CollectionView 中的物件巡覽](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md)。  
  
## 請參閱  
 [使用 XAML 排序和分組資料](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)