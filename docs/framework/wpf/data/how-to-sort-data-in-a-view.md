---
title: "如何：排序檢視中的資料 | Microsoft Docs"
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
  - "資料繫結, 在檢視中區分資料群組"
  - "資料繫結, 在檢視中排序資料"
  - "在檢視中區分資料群組"
  - "在檢視中排序資料"
  - "檢視, 分組資料"
  - "檢視, 排序資料"
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：排序檢視中的資料
這個範例說明如何排序檢視中的資料。  
  
## 範例  
 下列範例會建立簡單的 <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.Button>：  
  
 [!code-xml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式包含邏輯，可用以遞減順序排序 <xref:System.Windows.Controls.ListBox> 中的項目。  您可以這麼做的原因是因為以這樣的方式將項目加入至 <xref:System.Windows.Controls.ListBox> 會將它們加入至 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemCollection>，而 <xref:System.Windows.Controls.ItemCollection> 是從 <xref:System.Windows.Data.CollectionView> 類別衍生。  如果您要使用 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性將 <xref:System.Windows.Controls.ListBox> 繫結至集合，可以使用相同的排序技巧。  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 只要您有檢視物件的參考，就可以使用相同的技巧來排序其他集合檢視的內容。  如需如何取得檢視的範例，請參閱 [取得資料集合的預設檢視](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。  如需其他範例，請參閱 [在按一下行首時排序 GridView 資料行](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。  如需檢視的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)中的＜繫結至集合＞。  
  
 如需如何在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中套用排序邏輯的範例，請參閱 [使用 XAML 排序和分組資料](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)。  
  
## 請參閱  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>   
 [在按一下行首時排序 GridView 資料行](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [篩選檢視中的資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)