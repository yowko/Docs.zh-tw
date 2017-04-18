---
title: "如何：繫結至 LINQ 查詢結果 | Microsoft Docs"
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
  - "繫結至 LINQ 查詢結果 [WPF]"
  - "執行 LINQ 查詢 [WPF], 繫結至結果"
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：繫結至 LINQ 查詢結果
本範例示範如何執行 LINQ 查詢，然後再繫結到結果。  
  
## 範例  
 下列範例會建立兩個清單方塊。  第一個清單方塊包含三個清單項目。  
  
 [!code-xml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 從第一個清單方塊選取項目會叫用 \(Invoke\) 下列事件處理常式。  在這個範例中，`Tasks` 是 `Task` 物件的集合。  `Task` 類別 \(Class\) 具有名稱為 `Priority` 的屬性。  這個事件處理常式會執行 LINQ 查詢，以傳回具有所選優先順序值的 `Task` 物件集合，然後再將該集合設定為 <xref:System.Windows.FrameworkElement.DataContext%2A>。  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 第二個清單方塊會繫結到該集合，因為它的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 值是設定為 `{Binding}`。  因此，它會顯示傳回的集合 \(依據 `myTaskTemplate` <xref:System.Windows.DataTemplate>\)。  
  
## 請參閱  
 [讓資料可於 XAML 中繫結](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)   
 [繫結至集合並根據選取項目顯示資訊](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)   
 [WPF 4.5 版的新功能](../../../../docs/framework/wpf/getting-started/whats-new.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)