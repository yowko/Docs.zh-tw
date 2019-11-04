---
title: 如何：繫結至集合並根據選取項目顯示資訊
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
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459153"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="793da-102">如何：繫結至集合並根據選取項目顯示資訊</span><span class="sxs-lookup"><span data-stu-id="793da-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="793da-103">在簡單的主要詳細資料案例中，您有一個資料系結 <xref:System.Windows.Controls.ItemsControl>，例如 <xref:System.Windows.Controls.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="793da-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="793da-104">根據使用者選擇，您會顯示所選取專案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="793da-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="793da-105">這個範例會示範如何執行此案例。</span><span class="sxs-lookup"><span data-stu-id="793da-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="793da-106">範例</span><span class="sxs-lookup"><span data-stu-id="793da-106">Example</span></span>  
 <span data-ttu-id="793da-107">在此範例中，`People` 是 `Person` 類別的 <xref:System.Collections.ObjectModel.ObservableCollection%601>。</span><span class="sxs-lookup"><span data-stu-id="793da-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="793da-108">此 `Person` 類別包含三個屬性： `FirstName`、`LastName`和 `HomeTown`，所有類型 `string`。</span><span class="sxs-lookup"><span data-stu-id="793da-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="793da-109"><xref:System.Windows.Controls.ContentControl> 會使用下列定義如何呈現 `Person` 資訊的 <xref:System.Windows.DataTemplate>：</span><span class="sxs-lookup"><span data-stu-id="793da-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="793da-110">以下是此範例所產生之內容的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="793da-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="793da-111"><xref:System.Windows.Controls.ContentControl> 會顯示所選人員的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="793da-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="793da-112">![系結至集合](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="793da-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="793da-113">在此範例中要注意的兩件事包括：</span><span class="sxs-lookup"><span data-stu-id="793da-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="793da-114"><xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.ContentControl> 系結至相同的來源。</span><span class="sxs-lookup"><span data-stu-id="793da-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="793da-115">未指定這兩個系結的 <xref:System.Windows.Data.Binding.Path%2A> 屬性，因為這兩個控制項都系結至整個集合物件。</span><span class="sxs-lookup"><span data-stu-id="793da-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="793da-116">您必須將 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 屬性設定為 `true`，才能讓此作業正常執行。</span><span class="sxs-lookup"><span data-stu-id="793da-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="793da-117">設定這個屬性可確保選取的專案一律設定為 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="793da-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="793da-118">或者，如果 <xref:System.Windows.Controls.ListBox> 從 <xref:System.Windows.Data.CollectionViewSource>取得資料，則會自動同步處理選取範圍和貨幣。</span><span class="sxs-lookup"><span data-stu-id="793da-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="793da-119">請注意，`Person` 類別會以下列方式覆寫 `ToString` 方法。</span><span class="sxs-lookup"><span data-stu-id="793da-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="793da-120">根據預設，<xref:System.Windows.Controls.ListBox> 會呼叫 `ToString`，並在系結的集合中顯示每個物件的字串表示。</span><span class="sxs-lookup"><span data-stu-id="793da-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="793da-121">這就是為什麼每個 `Person` 會在 <xref:System.Windows.Controls.ListBox>中顯示為名字。</span><span class="sxs-lookup"><span data-stu-id="793da-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="793da-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="793da-122">See also</span></span>

- [<span data-ttu-id="793da-123">使用含階層式資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="793da-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="793da-124">使用含階層式 XML 資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="793da-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="793da-125">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="793da-125">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="793da-126">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="793da-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="793da-127">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="793da-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
