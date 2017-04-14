---
title: "如何：使用含階層式資料的主從式模式 | Microsoft Docs"
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
  - "資料繫結, 主從式資料開發架構"
  - "主從式資料開發架構"
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用含階層式資料的主從式模式
這個範例顯示如何實作主從式案例。  
  
## 範例  
 在這個範例中，`LeagueList` 是 `Leagues` 的集合。  每個 `League` 皆有一個 `Name` 與 `Divisions` 集合，而每個 `Division` 皆有一個名稱與 `Teams` 集合。  每個 `Team` 各有一個小組名稱。  
  
 [!code-xml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 以下是範例的螢幕擷取畫面。  `Divisions` <xref:System.Windows.Controls.ListBox> 會自動追蹤 `Leagues` <xref:System.Windows.Controls.ListBox> 中選取的項目，並顯示對應的資料。  `Teams` <xref:System.Windows.Controls.ListBox> 會追蹤其他兩個 <xref:System.Windows.Controls.ListBox> 控制項中選取的項目。  
  
 ![主從式範例](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 在這個範例中應該注意兩件事：  
  
1.  這三個 <xref:System.Windows.Controls.ListBox> 控制項都繫結至同一個來源。  您可以設定繫結的 <xref:System.Windows.Data.Binding.Path%2A> 屬性，以指定要讓 <xref:System.Windows.Controls.ListBox> 顯示的資料層級。  
  
2.  您必須對要追蹤選取項目的 <xref:System.Windows.Controls.ListBox> 控制項，將其 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 屬性設定為 `true`。  設定這個屬性，可確保選取的項目一律設定為 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。  不過，如果 <xref:System.Windows.Controls.ListBox> 是從 <xref:System.Windows.Data.CollectionViewSource> 取得其資料，則它會自動同步 \(Synchronize\) 選取項目與貨幣。  
  
 使用 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料時，這個方法會略有不同。  如需範例，請參閱 [使用含階層式 XML 資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)。  
  
## 請參閱  
 <xref:System.Windows.HierarchicalDataTemplate>   
 [繫結至集合並根據選取項目顯示資訊](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)