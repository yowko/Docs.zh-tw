---
title: HOW TO：繫結至 LINQ 查詢結果
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 9be0f95824c97456b50996f9cd6f010442b523f2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355944"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>HOW TO：繫結至 LINQ 查詢結果
此範例示範如何執行 LINQ 查詢，然後再繫結結果。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個清單方塊。 第一個清單方塊包含三個清單項目。  
  
 [!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 從第一個清單方塊中選取項目，就會叫用下列事件處理常式。 在此範例中，`Tasks`的集合`Task`物件。 `Task`類別具有名為`Priority`。 此事件處理常式會執行 LINQ 查詢，傳回的集合`Task`物件，選取的優先順序值，並再設定 as <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 第二個清單方塊繫結到該集合，因為其<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>值設定為`{Binding}`。 如此一來，它會顯示傳回的集合 (根據`myTaskTemplate` <xref:System.Windows.DataTemplate>)。  
  
## <a name="see-also"></a>另請參閱
- [讓資料可於 XAML 中繫結](how-to-make-data-available-for-binding-in-xaml.md)
- [繫結至集合並根據選取項目顯示資訊](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [WPF 第 4.5 版的新功能](../getting-started/whats-new.md)
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
