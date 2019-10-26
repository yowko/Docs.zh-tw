---
title: 如何：繫結至 LINQ 查詢結果
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 70f4b439d231d69e5671216bc4e62d0789ce66c7
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920127"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>如何：繫結至 LINQ 查詢結果

這個範例示範如何執行 LINQ 查詢，然後系結至結果。

## <a name="example"></a>範例

下列範例會建立兩個清單方塊。 第一個清單方塊包含三個清單專案。

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

從第一個清單方塊選取專案時，會叫用下列事件處理常式。 在此範例中，`Tasks` 是 `Task` 物件的集合。 `Task` 類別具有名為 `Priority`的屬性。 這個事件處理常式會執行 LINQ 查詢，以傳回具有所選優先順序值 `Task` 物件的集合，然後將其設定為 <xref:System.Windows.FrameworkElement.DataContext%2A>：

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

第二個清單方塊會系結至該集合，因為它的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 值設定為 `{Binding}`。 因此，它會顯示傳回的集合（根據 `myTaskTemplate` <xref:System.Windows.DataTemplate>）。

## <a name="see-also"></a>請參閱

- [讓資料可於 XAML 中繫結](how-to-make-data-available-for-binding-in-xaml.md)
- [繫結至集合並根據選取項目顯示資訊](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [WPF 第 4.5 版的新功能](../getting-started/whats-new.md)
- [資料繫結概觀](data-binding-overview.md)
