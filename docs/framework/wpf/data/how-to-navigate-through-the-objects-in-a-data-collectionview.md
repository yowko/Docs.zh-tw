---
title: "如何：透過資料 CollectionView 中的物件巡覽"
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
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f20881ed452f1ec78381d17a32b4cc2c77305e0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="20082-102">如何：透過資料 CollectionView 中的物件巡覽</span><span class="sxs-lookup"><span data-stu-id="20082-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="20082-103">檢視可讓在不同的方式，根據排序、 篩選或群組中檢視相同的資料集合。</span><span class="sxs-lookup"><span data-stu-id="20082-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="20082-104">檢視也會提供目前的記錄指標概念，並啟用移動指標。</span><span class="sxs-lookup"><span data-stu-id="20082-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="20082-105">這個範例示範如何取得目前的物件，以及巡覽資料集合，使用所提供的功能中的物件<xref:System.Windows.Data.CollectionView>類別。</span><span class="sxs-lookup"><span data-stu-id="20082-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20082-106">範例</span><span class="sxs-lookup"><span data-stu-id="20082-106">Example</span></span>  
 <span data-ttu-id="20082-107">在此範例中，`myCollectionView`是<xref:System.Windows.Data.CollectionView>是對繫結的集合檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="20082-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="20082-108">在下列範例中，`OnButton`事件處理常式`Previous`和`Next`按鈕應用程式中，也就是按鈕，好讓使用者巡覽資料集合。</span><span class="sxs-lookup"><span data-stu-id="20082-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="20082-109">請注意，<xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A>和<xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A>屬性報告是否在目前的記錄指標已有的開始和清單的結尾分別因此的<xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A>和<xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A>可以為適當地呼叫。</span><span class="sxs-lookup"><span data-stu-id="20082-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="20082-110"><xref:System.Windows.Data.CollectionView.CurrentItem%2A>檢視的屬性就會轉換為`Order`傳回集合中目前的訂單項目。</span><span class="sxs-lookup"><span data-stu-id="20082-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="20082-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20082-111">See Also</span></span>  
 [<span data-ttu-id="20082-112">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="20082-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="20082-113">排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="20082-113">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="20082-114">篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="20082-114">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="20082-115">使用 XAML 中的檢視排序和群組資料</span><span class="sxs-lookup"><span data-stu-id="20082-115">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="20082-116">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="20082-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
