---
title: 如何：使用含階層式資料的主從式模式
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 2e7d9ceed3ab8385f07d87ecdb92c0a99d410b40
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459089"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="58e79-102">如何：使用含階層式資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="58e79-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="58e79-103">這個範例示範如何執行主要-詳細資料案例。</span><span class="sxs-lookup"><span data-stu-id="58e79-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58e79-104">範例</span><span class="sxs-lookup"><span data-stu-id="58e79-104">Example</span></span>  
 <span data-ttu-id="58e79-105">在此範例中，`LeagueList` 是 `Leagues`的集合。</span><span class="sxs-lookup"><span data-stu-id="58e79-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="58e79-106">每個 `League` 都有一個 `Name` 和一個 `Divisions`的集合，而且每個 `Division` 都有一個名稱和一個 `Teams`的集合。</span><span class="sxs-lookup"><span data-stu-id="58e79-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="58e79-107">每個 `Team` 都有一個小組名稱。</span><span class="sxs-lookup"><span data-stu-id="58e79-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="58e79-108">以下是範例的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="58e79-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="58e79-109">`Divisions` <xref:System.Windows.Controls.ListBox> 會自動追蹤 `Leagues` <xref:System.Windows.Controls.ListBox> 中的選取專案，並顯示對應的資料。</span><span class="sxs-lookup"><span data-stu-id="58e79-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="58e79-110">`Teams` <xref:System.Windows.Controls.ListBox> 會追蹤其他兩個 <xref:System.Windows.Controls.ListBox> 控制項中的選取專案。</span><span class="sxs-lookup"><span data-stu-id="58e79-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![顯示主要&#45;詳細資料案例範例的螢幕擷取畫面。](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="58e79-112">在此範例中要注意的兩件事包括：</span><span class="sxs-lookup"><span data-stu-id="58e79-112">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="58e79-113">三個 <xref:System.Windows.Controls.ListBox> 控制項系結至相同的來源。</span><span class="sxs-lookup"><span data-stu-id="58e79-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="58e79-114">您可以設定系結的 <xref:System.Windows.Data.Binding.Path%2A> 屬性，以指定要讓 <xref:System.Windows.Controls.ListBox> 顯示的資料層級。</span><span class="sxs-lookup"><span data-stu-id="58e79-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2. <span data-ttu-id="58e79-115">您必須將 [<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>] 屬性設定為您要追蹤其選取範圍之 <xref:System.Windows.Controls.ListBox> 控制項上的 `true`。</span><span class="sxs-lookup"><span data-stu-id="58e79-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="58e79-116">設定這個屬性可確保選取的專案一律設定為 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="58e79-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="58e79-117">或者，如果 <xref:System.Windows.Controls.ListBox> 從 <xref:System.Windows.Data.CollectionViewSource>取得資料，則會自動同步處理選取範圍和貨幣。</span><span class="sxs-lookup"><span data-stu-id="58e79-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="58e79-118">當您使用 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料時，這項技術會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="58e79-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="58e79-119">如需範例，請參閱搭配[階層式 XML 資料使用主版-詳細模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="58e79-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e79-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="58e79-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="58e79-121">繫結至集合並根據選取項目顯示資訊</span><span class="sxs-lookup"><span data-stu-id="58e79-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="58e79-122">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="58e79-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="58e79-123">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="58e79-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="58e79-124">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="58e79-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
