---
title: "如何：處理路由事件 | Microsoft Docs"
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
  - "反昇事件"
  - "路由事件, 處理"
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 如何：處理路由事件
本範例顯示[反昇](GTMT)事件的運作方式，以及如何撰寫處理常式來處理[路由事件](GTMT)資料。  
  
## 範例  
 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，項目會排列成[項目樹狀結構](GTMT)。  父項目可參與處理一開始由項目樹狀結構中的子項目引發的事件。  可以這麼做是因為[事件路由](GTMT)的緣故。  
  
 路由事件通常會遵循兩種路由策略的其中一種，即[反昇](GTMT)或[通道](GTMT)。  這個範例將著重在[反昇](GTMT)事件，並使用 <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=fullName> 事件顯示路由的運作方式。  
  
 下列範例會建立兩個 <xref:System.Windows.Controls.Button> 控制項，並且使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性語法將事件處理常式附加到通用父項目，也就是這個範例中的 <xref:System.Windows.Controls.StackPanel>。  此範例不會針對每個 <xref:System.Windows.Controls.Button> 子項目附加個別事件處理常式，而是使用屬性語法附加事件處理常式到 <xref:System.Windows.Controls.StackPanel> 父項目。  這種事件處理模式顯示如何使用事件路由此一方式，來減少附加處理常式的目標項目數。  每個 <xref:System.Windows.Controls.Button> 的所有[反昇](GTMT)事件都會透過父項目路由。  
  
 請注意，在父 <xref:System.Windows.Controls.StackPanel> 項目上，指定為屬性的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件名稱是藉由命名 <xref:System.Windows.Controls.Button> 類別來部分限定的。  <xref:System.Windows.Controls.Button> 類別是 <xref:System.Windows.Controls.Primitives.ButtonBase> 衍生類別 \(Derived Class\)，在其成員清單中有 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  如果處理的事件不存在於路由事件處理常式所附加之項目的成員清單中，就必須使用這種部分限定的方式來附加事件處理常式。  
  
 [!code-xml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 下列範例會處理 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  此範例會報告哪個項目會處理事件和哪個項目會引發事件。  當使用者按下任一按鈕時，就會執行事件處理常式。  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## 請參閱  
 <xref:System.Windows.RoutedEvent>   
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)   
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)