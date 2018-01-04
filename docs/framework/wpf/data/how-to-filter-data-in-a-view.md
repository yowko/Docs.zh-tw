---
title: "如何：篩選檢視中的資料"
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
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17b7fc68319552a7b31d5eaf7826146de5c41aa5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="b4fb2-102">如何：篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="b4fb2-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="b4fb2-103">這個範例示範如何篩選檢視中的資料。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4fb2-104">範例</span><span class="sxs-lookup"><span data-stu-id="b4fb2-104">Example</span></span>  
 <span data-ttu-id="b4fb2-105">若要建立篩選，定義提供篩選的邏輯的方法。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="b4fb2-106">做為回呼方法，並接受類型的參數`object`。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="b4fb2-107">下列方法會傳回所有`Order`物件與`filled`屬性設定為 [否]，篩選出其餘的物件。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="b4fb2-108">然後，如下列範例所示，您可以套用篩選器。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="b4fb2-109">在此範例中，`myCollectionView`是<xref:System.Windows.Data.ListCollectionView>物件。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="b4fb2-110">若要復原篩選，您可以設定<xref:System.Windows.Data.CollectionView.Filter%2A>屬性`null`:</span><span class="sxs-lookup"><span data-stu-id="b4fb2-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="b4fb2-111">如需如何建立或取得的檢視資訊，請參閱[取得預設的檢視資料收集](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="b4fb2-112">完整的範例，請參閱[排序及篩選檢視範例中的項目](http://go.microsoft.com/fwlink/?LinkID=160040)。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-112">For the complete example, see [Sorting and Filtering Items in a View Sample](http://go.microsoft.com/fwlink/?LinkID=160040).</span></span>  
  
 <span data-ttu-id="b4fb2-113">如果您檢視物件來自於<xref:System.Windows.Data.CollectionViewSource>物件，您設定的事件處理常式來套用篩選邏輯<xref:System.Windows.Data.CollectionViewSource.Filter>事件。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="b4fb2-114">在下列範例中，`listingDataView`的執行個體<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="b4fb2-115">下列範例示範實作範例`ShowOnlyBargainsFilter`篩選事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="b4fb2-116">此事件處理常式使用<xref:System.Windows.Data.FilterEventArgs.Accepted%2A>屬性來篩選掉`AuctionItem`物件`CurrentPrice`為 $25 或更高。</span><span class="sxs-lookup"><span data-stu-id="b4fb2-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b4fb2-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4fb2-117">See Also</span></span>  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [<span data-ttu-id="b4fb2-118">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="b4fb2-118">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="b4fb2-119">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="b4fb2-119">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="b4fb2-120">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="b4fb2-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
