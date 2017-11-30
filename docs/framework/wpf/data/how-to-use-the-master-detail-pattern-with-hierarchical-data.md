---
title: "如何：使用含階層式資料的主從式模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb546a3429012a49ee7652a3470460935fc76d70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="92e29-102">如何：使用含階層式資料的主從式模式</span><span class="sxs-lookup"><span data-stu-id="92e29-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="92e29-103">這個範例示範如何實作的主檔/明細 」 案例。</span><span class="sxs-lookup"><span data-stu-id="92e29-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92e29-104">範例</span><span class="sxs-lookup"><span data-stu-id="92e29-104">Example</span></span>  
 <span data-ttu-id="92e29-105">在此範例中，`LeagueList`是一組`Leagues`。</span><span class="sxs-lookup"><span data-stu-id="92e29-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="92e29-106">每個`League`具有`Name`和集合`Divisions`，而且每個`Division`有一個名稱和集合`Teams`。</span><span class="sxs-lookup"><span data-stu-id="92e29-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="92e29-107">每個`Team`小組名稱。</span><span class="sxs-lookup"><span data-stu-id="92e29-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="92e29-108">以下是範例的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="92e29-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="92e29-109">`Divisions` <xref:System.Windows.Controls.ListBox>自動追蹤中的選取項目`Leagues`<xref:System.Windows.Controls.ListBox>並顯示對應的資料。</span><span class="sxs-lookup"><span data-stu-id="92e29-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="92e29-110">`Teams` <xref:System.Windows.Controls.ListBox>會追蹤其他兩個選取項目<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="92e29-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="92e29-111">![主要 &#45; 詳細資料範例](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="92e29-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="92e29-112">請注意，在此範例中的兩個事項如下：</span><span class="sxs-lookup"><span data-stu-id="92e29-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="92e29-113">三個<xref:System.Windows.Controls.ListBox>控制項繫結至相同的來源。</span><span class="sxs-lookup"><span data-stu-id="92e29-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="92e29-114">您設定<xref:System.Windows.Data.Binding.Path%2A>繫結來指定您想要的資料層級屬性<xref:System.Windows.Controls.ListBox>顯示。</span><span class="sxs-lookup"><span data-stu-id="92e29-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="92e29-115">您必須設定<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>屬性`true`上<xref:System.Windows.Controls.ListBox>控制項，其中您追蹤選取範圍。</span><span class="sxs-lookup"><span data-stu-id="92e29-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="92e29-116">設定這個屬性可確保已選取的項目一律會設為<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="92e29-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="92e29-117">或者，如果<xref:System.Windows.Controls.ListBox>取得它的資料<xref:System.Windows.Data.CollectionViewSource>，自動同步選取範圍和貨幣。</span><span class="sxs-lookup"><span data-stu-id="92e29-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="92e29-118">當您使用的技巧是稍有不同[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料。</span><span class="sxs-lookup"><span data-stu-id="92e29-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="92e29-119">如需範例，請參閱[階層式 XML 資料搭配使用主版詳細資料模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="92e29-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e29-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92e29-120">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="92e29-121">繫結至集合並根據選取項目顯示資訊</span><span class="sxs-lookup"><span data-stu-id="92e29-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="92e29-122">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="92e29-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="92e29-123">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="92e29-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="92e29-124">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="92e29-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
