---
title: 如何：繫結至 LINQ 查詢結果
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d21ac5f366e001ea76d6eda64ed62583248796f6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454410"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="94c97-102">如何：繫結至 LINQ 查詢結果</span><span class="sxs-lookup"><span data-stu-id="94c97-102">How to: Bind to the Results of a LINQ Query</span></span>

<span data-ttu-id="94c97-103">這個範例示範如何執行 LINQ 查詢，然後系結至結果。</span><span class="sxs-lookup"><span data-stu-id="94c97-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>

## <a name="example"></a><span data-ttu-id="94c97-104">範例</span><span class="sxs-lookup"><span data-stu-id="94c97-104">Example</span></span>

<span data-ttu-id="94c97-105">下列範例會建立兩個清單方塊。</span><span class="sxs-lookup"><span data-stu-id="94c97-105">The following example creates two list boxes.</span></span> <span data-ttu-id="94c97-106">第一個清單方塊包含三個清單專案。</span><span class="sxs-lookup"><span data-stu-id="94c97-106">The first list box contains three list items.</span></span>

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

<span data-ttu-id="94c97-107">從第一個清單方塊選取專案時，會叫用下列事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="94c97-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="94c97-108">在此範例中，`Tasks` 是 `Task` 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="94c97-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="94c97-109">`Task` 類別具有名為 `Priority`的屬性。</span><span class="sxs-lookup"><span data-stu-id="94c97-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="94c97-110">這個事件處理常式會執行 LINQ 查詢，以傳回具有所選優先順序值 `Task` 物件的集合，然後將其設定為 <xref:System.Windows.FrameworkElement.DataContext%2A>：</span><span class="sxs-lookup"><span data-stu-id="94c97-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

<span data-ttu-id="94c97-111">第二個清單方塊會系結至該集合，因為它的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 值設定為 `{Binding}`。</span><span class="sxs-lookup"><span data-stu-id="94c97-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="94c97-112">因此，它會顯示傳回的集合（根據 `myTaskTemplate` <xref:System.Windows.DataTemplate>）。</span><span class="sxs-lookup"><span data-stu-id="94c97-112">As a result, it displays the returned collection (based on the `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span></span>

## <a name="see-also"></a><span data-ttu-id="94c97-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="94c97-113">See also</span></span>

- [<span data-ttu-id="94c97-114">讓資料可於 XAML 中繫結</span><span class="sxs-lookup"><span data-stu-id="94c97-114">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
- [<span data-ttu-id="94c97-115">繫結至集合並根據選取項目顯示資訊</span><span class="sxs-lookup"><span data-stu-id="94c97-115">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="94c97-116">WPF 第 4.5 版的新功能</span><span class="sxs-lookup"><span data-stu-id="94c97-116">What's New in WPF Version 4.5</span></span>](../getting-started/whats-new.md)
- [<span data-ttu-id="94c97-117">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="94c97-117">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
