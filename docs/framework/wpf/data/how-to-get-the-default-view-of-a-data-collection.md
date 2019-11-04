---
title: 如何：取得資料集合的預設檢視
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: e82d252ed82e4d2e6d641e8b60e890cc93bb0427
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459125"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="1cceb-102">如何：取得資料集合的預設檢視</span><span class="sxs-lookup"><span data-stu-id="1cceb-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="1cceb-103">Views 可以根據排序、篩選或群組準則，以不同的方式來查看相同的資料收集。</span><span class="sxs-lookup"><span data-stu-id="1cceb-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="1cceb-104">每個集合都有一個共用的預設 view，當系結將集合指定為其來源時，它會當做實際的系結來源使用。</span><span class="sxs-lookup"><span data-stu-id="1cceb-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="1cceb-105">這個範例會示範如何取得集合的預設視圖。</span><span class="sxs-lookup"><span data-stu-id="1cceb-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cceb-106">範例</span><span class="sxs-lookup"><span data-stu-id="1cceb-106">Example</span></span>  
 <span data-ttu-id="1cceb-107">若要建立此視圖，您需要集合的物件參考。</span><span class="sxs-lookup"><span data-stu-id="1cceb-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="1cceb-108">您可以藉由參考您自己的程式碼後置物件、取得資料內容、取得資料來源的屬性，或取得系結的屬性，來取得此資料物件。</span><span class="sxs-lookup"><span data-stu-id="1cceb-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="1cceb-109">這個範例會示範如何取得資料物件的 <xref:System.Windows.FrameworkElement.DataContext%2A>，並使用它來直接取得此集合的預設集合視圖。</span><span class="sxs-lookup"><span data-stu-id="1cceb-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="1cceb-110">在此範例中，根項目是 <xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="1cceb-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="1cceb-111"><xref:System.Windows.FrameworkElement.DataContext%2A> 會設定為*mydatasource (* ，這會參考屬於*Order*物件 <xref:System.Collections.ObjectModel.ObservableCollection%601> 的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="1cceb-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="1cceb-112">或者，您可以使用 <xref:System.Windows.Data.CollectionViewSource> 類別，具現化和系結至您自己的集合視圖。</span><span class="sxs-lookup"><span data-stu-id="1cceb-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="1cceb-113">這個集合視圖只會由直接系結至它的控制項共用。</span><span class="sxs-lookup"><span data-stu-id="1cceb-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="1cceb-114">如需範例，請參閱資料系結[總覽](../../../desktop-wpf/data/data-binding-overview.md)中的如何建立視圖一節。</span><span class="sxs-lookup"><span data-stu-id="1cceb-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="1cceb-115">如需集合視圖所提供之功能的範例，請參閱[排序視圖](how-to-sort-data-in-a-view.md)中的資料、[篩選視圖中的資料](how-to-filter-data-in-a-view.md)，以及[流覽資料 CollectionView 中的物件](how-to-navigate-through-the-objects-in-a-data-collectionview.md)。</span><span class="sxs-lookup"><span data-stu-id="1cceb-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](how-to-sort-data-in-a-view.md), [Filter Data in a View](how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cceb-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="1cceb-116">See also</span></span>

- [<span data-ttu-id="1cceb-117">使用 XAML 中的檢視排序和群組資料</span><span class="sxs-lookup"><span data-stu-id="1cceb-117">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="1cceb-118">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="1cceb-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
