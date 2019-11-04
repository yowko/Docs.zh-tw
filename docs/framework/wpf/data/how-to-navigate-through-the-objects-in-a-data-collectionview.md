---
title: 如何：透過資料 CollectionView 中的物件巡覽
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459701"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="2033c-102">如何：透過資料 CollectionView 中的物件巡覽</span><span class="sxs-lookup"><span data-stu-id="2033c-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="2033c-103">Views 可以根據排序、篩選或群組，以不同的方式來查看相同的資料收集。</span><span class="sxs-lookup"><span data-stu-id="2033c-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="2033c-104">Views 也提供目前的記錄指標概念，並可讓您移動指標。</span><span class="sxs-lookup"><span data-stu-id="2033c-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="2033c-105">這個範例示範如何使用 <xref:System.Windows.Data.CollectionView> 類別中提供的功能，取得目前的物件，以及流覽資料集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="2033c-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2033c-106">範例</span><span class="sxs-lookup"><span data-stu-id="2033c-106">Example</span></span>  
 <span data-ttu-id="2033c-107">在此範例中，`myCollectionView` 是 <xref:System.Windows.Data.CollectionView> 物件，其為系結集合的 view。</span><span class="sxs-lookup"><span data-stu-id="2033c-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="2033c-108">在下列範例中，`OnButton` 是應用程式中 [`Previous`] 和 [`Next`] 按鈕的事件處理常式，這是允許使用者導覽資料收集的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2033c-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="2033c-109">請注意，<xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> 和 <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> 屬性會報告目前的記錄指標是否分別來自于清單的開頭和結尾，以便能夠適當地呼叫 <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> 和 <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A>。</span><span class="sxs-lookup"><span data-stu-id="2033c-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="2033c-110">視圖的 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> 屬性會轉換為 `Order`，以傳回集合中目前的訂單專案。</span><span class="sxs-lookup"><span data-stu-id="2033c-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="2033c-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="2033c-111">See also</span></span>

- [<span data-ttu-id="2033c-112">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="2033c-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="2033c-113">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="2033c-113">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="2033c-114">篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="2033c-114">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="2033c-115">使用 XAML 中的檢視排序和群組資料</span><span class="sxs-lookup"><span data-stu-id="2033c-115">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="2033c-116">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="2033c-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
