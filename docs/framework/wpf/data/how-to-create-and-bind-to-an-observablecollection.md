---
title: "如何：建立和繫結至 ObservableCollection | Microsoft Docs"
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
  - "類別, ObservableCollection"
  - "資料繫結, ObservableCollection 類別"
  - "告知"
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：建立和繫結至 ObservableCollection
這個範例顯示如何建立和繫結至衍生自 <xref:System.Collections.ObjectModel.ObservableCollection%601> 類別的集合，這個集合類別會在加入或移除項目時提供告知。  
  
## 範例  
 下列範例顯示 `NameList` 集合的實作：  
  
 [!code-csharp[MultiBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[MultiBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameList.vb#1)]  
  
 您可以使用讓其他 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件變為可用的相同方式，將集合變為可用來進行繫結 \(如 [讓資料可於 XAML 中繫結](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)中所述\)。  例如，您可以使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 具現化 \(Instantiate\) 集合，並將集合指定為資源 \(如這裡所示\)：  
  
 [!code-xml[MultiBinding#OCHowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#ochowto)]  
[!code-xml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
  
 然後，就可以繫結至集合：  
  
 [!code-xml[MultiBinding#MultiBindingListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindinglistbox)]  
  
 這裡並未顯示 `NameItemTemplate` 的定義。  
  
> [!NOTE]
>  集合中的物件必須滿足[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)中所述的需求。  尤其是如果使用 <xref:System.Windows.Data.BindingMode> 或 <xref:System.Windows.Data.BindingMode> \(例如，想要在來源屬性動態變更時更新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]\)，則必須實作適合的屬性變更告知機制 \(如 <xref:System.ComponentModel.INotifyPropertyChanged> 介面\)。  
  
 如需詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)中的＜繫結至集合＞一節。  
  
## 請參閱  
 [排序檢視中的資料](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [篩選檢視中的資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [使用 XAML 排序和分組資料](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)