---
title: HOW TO：巡覽資料 CollectionView 中的所有物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 1507ab4db0c91b670d8bca754f6fd67d887c7041
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138173"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="281f0-102">HOW TO：巡覽資料 CollectionView 中的所有物件</span><span class="sxs-lookup"><span data-stu-id="281f0-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="281f0-103">檢視可讓在不同的方式，取決於排序、 篩選或群組中檢視相同的資料收集。</span><span class="sxs-lookup"><span data-stu-id="281f0-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="281f0-104">檢視也會提供目前記錄指標的概念，並啟用移動指標。</span><span class="sxs-lookup"><span data-stu-id="281f0-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="281f0-105">此範例示範如何取得目前的物件，以及透過使用中提供的功能資料集合中的物件巡覽<xref:System.Windows.Data.CollectionView>類別。</span><span class="sxs-lookup"><span data-stu-id="281f0-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="281f0-106">範例</span><span class="sxs-lookup"><span data-stu-id="281f0-106">Example</span></span>  
 <span data-ttu-id="281f0-107">在此範例中，`myCollectionView`是<xref:System.Windows.Data.CollectionView>對繫結的集合是一種檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="281f0-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="281f0-108">在下列範例中，`OnButton`事件處理常式`Previous`和`Next`按鈕在應用程式，也就是按鈕，可讓使用者導覽資料收集。</span><span class="sxs-lookup"><span data-stu-id="281f0-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="281f0-109">請注意，<xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A>並<xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A>屬性會報告是否目前記錄指標已有的開始和清單的結尾分別因此，<xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A>和<xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A>可以為適當地呼叫。</span><span class="sxs-lookup"><span data-stu-id="281f0-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="281f0-110"><xref:System.Windows.Data.CollectionView.CurrentItem%2A>檢視的屬性，這會轉換為`Order`返回目前的訂單項目集合中。</span><span class="sxs-lookup"><span data-stu-id="281f0-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="281f0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="281f0-111">See also</span></span>

- [<span data-ttu-id="281f0-112">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="281f0-112">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="281f0-113">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="281f0-113">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="281f0-114">篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="281f0-114">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="281f0-115">使用 XAML 中的檢視排序和分組資料</span><span class="sxs-lookup"><span data-stu-id="281f0-115">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="281f0-116">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="281f0-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
