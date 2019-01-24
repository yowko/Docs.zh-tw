---
title: HOW TO：實作 GridView 之 ListView 中的群組項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 1570eab70dae690f508975162b7553de92be6f12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664352"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="541f6-102">HOW TO：實作 GridView 之 ListView 中的群組項目</span><span class="sxs-lookup"><span data-stu-id="541f6-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="541f6-103">此範例示範如何顯示群組中的項目數<xref:System.Windows.Controls.GridView>檢視模式<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="541f6-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="541f6-104">範例</span><span class="sxs-lookup"><span data-stu-id="541f6-104">Example</span></span>  
 <span data-ttu-id="541f6-105">若要顯示群組中的項目數<xref:System.Windows.Controls.ListView>，定義<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="541f6-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="541f6-106">下列範例所示<xref:System.Windows.Data.CollectionViewSource>群組資料項目的值根據`Catalog`資料欄位。</span><span class="sxs-lookup"><span data-stu-id="541f6-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="541f6-107">下列範例會設定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>for<xref:System.Windows.Controls.ListView>到<xref:System.Windows.Data.CollectionViewSource>前一個範例定義。</span><span class="sxs-lookup"><span data-stu-id="541f6-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="541f6-108">此範例也會定義<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>實作<xref:System.Windows.Controls.Expander>控制項。</span><span class="sxs-lookup"><span data-stu-id="541f6-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="541f6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="541f6-109">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="541f6-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="541f6-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [<span data-ttu-id="541f6-111">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="541f6-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
- [<span data-ttu-id="541f6-112">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="541f6-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
