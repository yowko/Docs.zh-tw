---
title: "如何：實作 CompositeCollection | Microsoft Docs"
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
  - "類別, CompositeCollection"
  - "資料繫結, CompositeCollection 類別"
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：實作 CompositeCollection
## 範例  
 下列範例顯示如何使用 <xref:System.Windows.Data.CompositeCollection> 類別將多個集合和項目顯示為一份清單。  在這個範例中，`GreekGods` 為 `GreekGod` 自訂物件的 <xref:System.Collections.ObjectModel.ObservableCollection%601>。  資料範本已定義成將 `GreekGod` 物件和 `GreekHero` 物件分別以金色和青色的前景色彩呈現。  
  
 [!code-xml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## 請參閱  
 <xref:System.Windows.Data.CollectionContainer>   
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>   
 <xref:System.Windows.Data.XmlDataProvider>   
 <xref:System.Windows.DataTemplate>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)