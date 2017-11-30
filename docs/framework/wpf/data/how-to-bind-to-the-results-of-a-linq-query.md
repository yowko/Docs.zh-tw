---
title: "如何：繫結至 LINQ 查詢結果"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e77a0c698dae0330877c54422c15e14c82376891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>如何：繫結至 LINQ 查詢結果
此範例示範如何執行 LINQ 查詢，然後再繫結結果。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個清單方塊。 第一個清單方塊包含三個清單項目。  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 從第一個清單方塊中選取項目，就會叫用下列事件處理常式。 在此範例中，`Tasks`是一組`Task`物件。 `Task`類別具有內容，名為`Priority`。 這個事件處理常式執行 LINQ 查詢傳回之集合的`Task`物件具有選定的優先順序的值，並設定它作為<xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 第二個清單方塊會繫結至該集合，因為其<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>值設定為`{Binding}`。 如此一來，它會顯示傳回的集合 (根據`myTaskTemplate` <xref:System.Windows.DataTemplate>)。  
  
## <a name="see-also"></a>另請參閱  
 [讓資料可於 XAML 中繫結](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [繫結至集合並根據選取項目顯示資訊](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [WPF 第 4.5 版的新功能](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
