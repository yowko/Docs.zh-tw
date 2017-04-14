---
title: "如何：尋找 DataTemplate 產生的項目 | Microsoft Docs"
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
  - "DataTemplate"
  - "尋找 DataTemplate 項目"
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：尋找 DataTemplate 產生的項目
這個範例顯示如何尋找 <xref:System.Windows.DataTemplate> 產生的項目。  
  
## 範例  
 這個範例中有一個 <xref:System.Windows.Controls.ListBox> 已繫結至某些 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料：  
  
 [!code-xml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> 會使用下列 <xref:System.Windows.DataTemplate>：  
  
 [!code-xml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 如果您想擷取由特定 <xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.DataTemplate> 所產生的 <xref:System.Windows.Controls.TextBlock> 項目，就需要取得 <xref:System.Windows.Controls.ListBoxItem>，找到這個 <xref:System.Windows.Controls.ListBoxItem> 中的 <xref:System.Windows.Controls.ContentPresenter>，再呼叫在這個 <xref:System.Windows.Controls.ContentPresenter> 上設定之 <xref:System.Windows.DataTemplate> 上的 <xref:System.Windows.FrameworkTemplate.FindName%2A>。  下列範例顯示如何執行這些步驟。  為了便於示範，這個範例會建立訊息方塊，其中顯示 <xref:System.Windows.DataTemplate> 產生的文字區塊的文字內容。  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 以下是 `FindVisualChild` 的實作，其中用到了 <xref:System.Windows.Media.VisualTreeHelper> 方法：  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## 請參閱  
 [如何：尋找 ControlTemplate 產生的項目](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [WPF XAML 名稱範圍](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)   
 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)