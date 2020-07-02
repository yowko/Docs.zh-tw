---
title: 如何：繫結至集合並根據選取項目顯示資訊
description: 請遵循此範例來瞭解如何系結至集合，並根據 Windows Presentation Foundation （WPF）中的選取範圍來顯示資訊。
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619607"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="b0b5c-103">如何：繫結至集合並根據選取項目顯示資訊</span><span class="sxs-lookup"><span data-stu-id="b0b5c-103">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="b0b5c-104">在簡單的主版詳細案例中，您有資料系結， <xref:System.Windows.Controls.ItemsControl> 例如 <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-104">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="b0b5c-105">根據使用者選擇，您會顯示所選取專案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-105">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="b0b5c-106">這個範例會示範如何執行此案例。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-106">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0b5c-107">範例</span><span class="sxs-lookup"><span data-stu-id="b0b5c-107">Example</span></span>  
 <span data-ttu-id="b0b5c-108">在此範例中， `People` 是 <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` 類別的。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-108">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="b0b5c-109">這個 `Person` 類別包含三個屬性： `FirstName` 、 `LastName` 和 `HomeTown` ，全都是型別 `string` 。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-109">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="b0b5c-110"><xref:System.Windows.Controls.ContentControl>會使用下列 <xref:System.Windows.DataTemplate> 定義呈現資訊的方式 `Person` ：</span><span class="sxs-lookup"><span data-stu-id="b0b5c-110">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="b0b5c-111">以下是此範例所產生之內容的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-111">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="b0b5c-112">會 <xref:System.Windows.Controls.ContentControl> 顯示所選人員的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-112">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="b0b5c-113">![繫結至集合](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="b0b5c-113">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="b0b5c-114">在此範例中要注意的兩件事包括：</span><span class="sxs-lookup"><span data-stu-id="b0b5c-114">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="b0b5c-115"><xref:System.Windows.Controls.ListBox>和系結 <xref:System.Windows.Controls.ContentControl> 至相同的來源。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-115">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="b0b5c-116"><xref:System.Windows.Data.Binding.Path%2A>未指定這兩個系結的屬性，因為這兩個控制項都系結至整個集合物件。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-116">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="b0b5c-117">您必須將屬性設定為，才能 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> `true` 讓此作業正常執行。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-117">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="b0b5c-118">設定這個屬性可確保選取的專案一律設定為 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-118">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="b0b5c-119">或者，如果 <xref:System.Windows.Controls.ListBox> 從取得資料 <xref:System.Windows.Data.CollectionViewSource> ，它會自動同步處理選取範圍和貨幣。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-119">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="b0b5c-120">請注意， `Person` 類別會以 `ToString` 下列方式覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-120">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="b0b5c-121">根據預設，會 <xref:System.Windows.Controls.ListBox> 呼叫 `ToString` 並顯示系結集合中每個物件的字串表示。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-121">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="b0b5c-122">這就是為什麼每個 `Person` 都會顯示為中的名字 <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="b0b5c-122">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="b0b5c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0b5c-123">See also</span></span>

- [<span data-ttu-id="b0b5c-124">搭配階層式資料使用主版-詳細模式</span><span class="sxs-lookup"><span data-stu-id="b0b5c-124">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="b0b5c-125">搭配階層式 XML 資料使用主版-詳細模式</span><span class="sxs-lookup"><span data-stu-id="b0b5c-125">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="b0b5c-126">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="b0b5c-126">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="b0b5c-127">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="b0b5c-127">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="b0b5c-128">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="b0b5c-128">How-to Topics</span></span>](data-binding-how-to-topics.md)
