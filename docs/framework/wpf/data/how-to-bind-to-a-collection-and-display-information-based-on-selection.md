---
title: HOW TO：繫結至集合並根據選取項目顯示資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 549f4e7af1a9aa623c7f8ff12b528f771a8ff806
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504768"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="2d072-102">HOW TO：繫結至集合並根據選取項目顯示資訊</span><span class="sxs-lookup"><span data-stu-id="2d072-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="2d072-103">在簡單的主版詳細資料案例中，您會有資料繫結<xref:System.Windows.Controls.ItemsControl>這類<xref:System.Windows.Controls.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="2d072-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="2d072-104">您根據使用者選取項目，顯示有關所選項目的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2d072-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="2d072-105">此範例示範如何實作此案例。</span><span class="sxs-lookup"><span data-stu-id="2d072-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d072-106">範例</span><span class="sxs-lookup"><span data-stu-id="2d072-106">Example</span></span>  
 <span data-ttu-id="2d072-107">在此範例中，`People`已<xref:System.Collections.ObjectModel.ObservableCollection%601>的`Person`類別。</span><span class="sxs-lookup"><span data-stu-id="2d072-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="2d072-108">這`Person`類別包含三個屬性： `FirstName`， `LastName`，以及`HomeTown`，所有型別的`string`。</span><span class="sxs-lookup"><span data-stu-id="2d072-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="2d072-109"><xref:System.Windows.Controls.ContentControl>會使用下列<xref:System.Windows.DataTemplate>的定義方式的資訊`Person`呈現：</span><span class="sxs-lookup"><span data-stu-id="2d072-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="2d072-110">以下是範例所產生的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="2d072-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="2d072-111"><xref:System.Windows.Controls.ContentControl>顯示選取之人員的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="2d072-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="2d072-112">![繫結至集合](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="2d072-112">![Binding to a collection](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="2d072-113">請注意，在此範例中的兩個事項如下：</span><span class="sxs-lookup"><span data-stu-id="2d072-113">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="2d072-114"><xref:System.Windows.Controls.ListBox>而<xref:System.Windows.Controls.ContentControl>繫結至相同的來源。</span><span class="sxs-lookup"><span data-stu-id="2d072-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="2d072-115"><xref:System.Windows.Data.Binding.Path%2A>因為兩個控制項都繫結至整個集合物件未指定這兩個繫結的屬性。</span><span class="sxs-lookup"><span data-stu-id="2d072-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2.  <span data-ttu-id="2d072-116">您必須設定<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>屬性設`true`才能運作。</span><span class="sxs-lookup"><span data-stu-id="2d072-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="2d072-117">設定這個屬性可確保已選取的項目一律會設為<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="2d072-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="2d072-118">或者，如果<xref:System.Windows.Controls.ListBox>取得其資料從<xref:System.Windows.Data.CollectionViewSource>，自動同步選取項目和貨幣。</span><span class="sxs-lookup"><span data-stu-id="2d072-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="2d072-119">請注意，`Person`類別會覆寫`ToString`方法以下列方式。</span><span class="sxs-lookup"><span data-stu-id="2d072-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="2d072-120">根據預設，<xref:System.Windows.Controls.ListBox>呼叫`ToString`和顯示繫結集合中的每個物件的字串表示。</span><span class="sxs-lookup"><span data-stu-id="2d072-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="2d072-121">這就是為什麼每個`Person`會顯示中的第一個名稱為<xref:System.Windows.Controls.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="2d072-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="2d072-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d072-122">See also</span></span>
- [<span data-ttu-id="2d072-123">使用含階層式資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="2d072-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="2d072-124">使用含階層式 XML 資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="2d072-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="2d072-125">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="2d072-125">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="2d072-126">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="2d072-126">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [<span data-ttu-id="2d072-127">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="2d072-127">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
