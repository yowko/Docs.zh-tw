---
title: HOW TO：篩選檢視中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: 33af517c086f8f89cc06a1de7a2979c5b1624109
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689311"
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="fefd0-102">HOW TO：篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="fefd0-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="fefd0-103">此範例示範如何篩選檢視中的資料。</span><span class="sxs-lookup"><span data-stu-id="fefd0-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fefd0-104">範例</span><span class="sxs-lookup"><span data-stu-id="fefd0-104">Example</span></span>  
 <span data-ttu-id="fefd0-105">若要建立篩選，定義方法，提供篩選邏輯。</span><span class="sxs-lookup"><span data-stu-id="fefd0-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="fefd0-106">做為回呼方法，並接受類型參數的`object`。</span><span class="sxs-lookup"><span data-stu-id="fefd0-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="fefd0-107">下列方法會傳回所有`Order`具有物件`filled`屬性設定為 [否]，篩選出其餘的物件。</span><span class="sxs-lookup"><span data-stu-id="fefd0-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="fefd0-108">您接著可以套用篩選器，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fefd0-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="fefd0-109">在此範例中，`myCollectionView`是<xref:System.Windows.Data.ListCollectionView>物件。</span><span class="sxs-lookup"><span data-stu-id="fefd0-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="fefd0-110">若要復原篩選，您可以設定<xref:System.Windows.Data.CollectionView.Filter%2A>屬性設`null`:</span><span class="sxs-lookup"><span data-stu-id="fefd0-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="fefd0-111">如需有關如何建立或取得檢視的資訊，請參閱 <<c0> [ 取得資料集合的預設檢視](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="fefd0-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="fefd0-112">完整的範例，請參閱[排序及篩選檢視的範例中的項目](https://go.microsoft.com/fwlink/?LinkID=160040)。</span><span class="sxs-lookup"><span data-stu-id="fefd0-112">For the complete example, see [Sorting and Filtering Items in a View Sample](https://go.microsoft.com/fwlink/?LinkID=160040).</span></span>  
  
 <span data-ttu-id="fefd0-113">如果您檢視的物件是來自<xref:System.Windows.Data.CollectionViewSource>物件，您設定的事件處理常式來套用篩選邏輯<xref:System.Windows.Data.CollectionViewSource.Filter>事件。</span><span class="sxs-lookup"><span data-stu-id="fefd0-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="fefd0-114">在下列範例中，`listingDataView`的執行個體<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="fefd0-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="fefd0-115">下圖顯示的範例實作`ShowOnlyBargainsFilter`篩選事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="fefd0-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="fefd0-116">這個事件處理常式會使用<xref:System.Windows.Data.FilterEventArgs.Accepted%2A>屬性來篩選掉`AuctionItem`具有物件`CurrentPrice`$25 個或更高。</span><span class="sxs-lookup"><span data-stu-id="fefd0-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="fefd0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fefd0-117">See also</span></span>
- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [<span data-ttu-id="fefd0-118">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="fefd0-118">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="fefd0-119">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="fefd0-119">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="fefd0-120">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="fefd0-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
