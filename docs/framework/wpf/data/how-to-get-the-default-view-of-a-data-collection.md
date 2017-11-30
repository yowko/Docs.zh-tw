---
title: "如何：取得資料集合的預設檢視"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d1ababcb7a00496b59005b5e90f875511fefc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="145bc-102">如何：取得資料集合的預設檢視</span><span class="sxs-lookup"><span data-stu-id="145bc-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="145bc-103">檢視可讓在不同的方式，根據排序、 篩選或群組準則中檢視相同的資料集合。</span><span class="sxs-lookup"><span data-stu-id="145bc-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="145bc-104">每個集合有一個共用的預設檢視，可做為實際的繫結來源時繫結指定作為其來源集合。</span><span class="sxs-lookup"><span data-stu-id="145bc-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="145bc-105">這個範例示範如何取得集合的預設檢視。</span><span class="sxs-lookup"><span data-stu-id="145bc-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="145bc-106">範例</span><span class="sxs-lookup"><span data-stu-id="145bc-106">Example</span></span>  
 <span data-ttu-id="145bc-107">若要建立檢視，您需要將集合的物件參考。</span><span class="sxs-lookup"><span data-stu-id="145bc-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="145bc-108">可以藉由取得資料內容，取得屬性的資料來源，或取得繫結的屬性來參考您自己的程式碼後置物件，取得這個資料物件。</span><span class="sxs-lookup"><span data-stu-id="145bc-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="145bc-109">這個範例示範如何取得<xref:System.Windows.FrameworkElement.DataContext%2A>資料物件和使用，以直接取得預設集合檢視此集合。</span><span class="sxs-lookup"><span data-stu-id="145bc-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="145bc-110">在此範例中，根項目是<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="145bc-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="145bc-111"><xref:System.Windows.FrameworkElement.DataContext%2A>設*myDataSource*，這指的是資料提供者<xref:System.Collections.ObjectModel.ObservableCollection%601>的*順序*物件。</span><span class="sxs-lookup"><span data-stu-id="145bc-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="145bc-112">或者，您可以具現化，並繫結至您的集合檢視使用<xref:System.Windows.Data.CollectionViewSource>類別。</span><span class="sxs-lookup"><span data-stu-id="145bc-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="145bc-113">此集合檢視只會共用直接繫結至它的控制項。</span><span class="sxs-lookup"><span data-stu-id="145bc-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="145bc-114">如需範例，請參閱 「 如何 」 主題中的檢視建立[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="145bc-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="145bc-115">集合檢視所提供之功能的範例，請參閱[檢視中排序資料](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)，[檢視中的篩選資料](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)，和[瀏覽到中的物件資料 CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="145bc-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="145bc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="145bc-116">See Also</span></span>  
 [<span data-ttu-id="145bc-117">使用 XAML 中的檢視排序和群組資料</span><span class="sxs-lookup"><span data-stu-id="145bc-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="145bc-118">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="145bc-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
