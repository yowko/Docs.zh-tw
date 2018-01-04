---
title: "如何：繫結至集合並根據選取項目顯示資訊"
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
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a751025470b566ef1e735e4ddd192cfd8fc354ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="39593-102">如何：繫結至集合並根據選取項目顯示資訊</span><span class="sxs-lookup"><span data-stu-id="39593-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="39593-103">在簡單的主版詳細資料案例中，您必須要有資料繫結<xref:System.Windows.Controls.ItemsControl>例如<xref:System.Windows.Controls.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="39593-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="39593-104">您根據使用者選取項目，顯示有關所選項目的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="39593-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="39593-105">這個範例示範如何實作此案例。</span><span class="sxs-lookup"><span data-stu-id="39593-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39593-106">範例</span><span class="sxs-lookup"><span data-stu-id="39593-106">Example</span></span>  
 <span data-ttu-id="39593-107">在此範例中，`People`是<xref:System.Collections.ObjectModel.ObservableCollection%601>的`Person`類別。</span><span class="sxs-lookup"><span data-stu-id="39593-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="39593-108">這`Person`類別包含三個屬性： `FirstName`， `LastName`，和`HomeTown`，所有的型別`string`。</span><span class="sxs-lookup"><span data-stu-id="39593-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="39593-109"><xref:System.Windows.Controls.ContentControl>會使用下列<xref:System.Windows.DataTemplate>，定義方式的資訊`Person`呈現：</span><span class="sxs-lookup"><span data-stu-id="39593-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="39593-110">以下是這個範例會產生的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="39593-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="39593-111"><xref:System.Windows.Controls.ContentControl>顯示選取之人員的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="39593-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="39593-112">![繫結至集合](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="39593-112">![Binding to a collection](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="39593-113">請注意，在此範例中的兩個事項如下：</span><span class="sxs-lookup"><span data-stu-id="39593-113">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="39593-114"><xref:System.Windows.Controls.ListBox>和<xref:System.Windows.Controls.ContentControl>繫結至相同的來源。</span><span class="sxs-lookup"><span data-stu-id="39593-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="39593-115"><xref:System.Windows.Data.Binding.Path%2A>由於兩個控制項要繫結至整個集合物件未指定這兩個繫結的屬性。</span><span class="sxs-lookup"><span data-stu-id="39593-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2.  <span data-ttu-id="39593-116">您必須設定<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>屬性`true`，才能順利運作。</span><span class="sxs-lookup"><span data-stu-id="39593-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="39593-117">設定這個屬性可確保已選取的項目一律會設為<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="39593-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="39593-118">或者，如果<xref:System.Windows.Controls.ListBox>取得它的資料<xref:System.Windows.Data.CollectionViewSource>，自動同步選取範圍和貨幣。</span><span class="sxs-lookup"><span data-stu-id="39593-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="39593-119">請注意，`Person`類別覆寫`ToString`方法以下列方式。</span><span class="sxs-lookup"><span data-stu-id="39593-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="39593-120">根據預設，<xref:System.Windows.Controls.ListBox>呼叫`ToString`並顯示每個物件的字串表示，此繫結集合中。</span><span class="sxs-lookup"><span data-stu-id="39593-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="39593-121">這就是為什麼每個`Person`顯示中的第一個名稱為<xref:System.Windows.Controls.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="39593-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="39593-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="39593-122">See Also</span></span>  
 [<span data-ttu-id="39593-123">使用含階層式資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="39593-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [<span data-ttu-id="39593-124">使用含階層式 XML 資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="39593-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [<span data-ttu-id="39593-125">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="39593-125">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="39593-126">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="39593-126">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="39593-127">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="39593-127">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
