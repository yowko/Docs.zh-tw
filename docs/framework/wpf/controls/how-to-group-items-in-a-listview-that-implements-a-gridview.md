---
title: 如何：實作 GridView 的 ListView 中的群組項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 76074449d4ea1454689c51ecad54d7c495f00872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551904"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="a21dd-102">如何：實作 GridView 的 ListView 中的群組項目</span><span class="sxs-lookup"><span data-stu-id="a21dd-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="a21dd-103">這個範例示範如何顯示群組中的項目<xref:System.Windows.Controls.GridView>檢視模式<xref:System.Windows.Controls.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="a21dd-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a21dd-104">範例</span><span class="sxs-lookup"><span data-stu-id="a21dd-104">Example</span></span>  
 <span data-ttu-id="a21dd-105">若要顯示群組中的項目<xref:System.Windows.Controls.ListView>，定義<xref:System.Windows.Data.CollectionViewSource>。</span><span class="sxs-lookup"><span data-stu-id="a21dd-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="a21dd-106">下列範例所示<xref:System.Windows.Data.CollectionViewSource>，群組資料項目的值根據`Catalog`資料欄位。</span><span class="sxs-lookup"><span data-stu-id="a21dd-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="a21dd-107">下列範例會設定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>如<xref:System.Windows.Controls.ListView>至<xref:System.Windows.Data.CollectionViewSource>前一個範例定義。</span><span class="sxs-lookup"><span data-stu-id="a21dd-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="a21dd-108">此範例也會定義<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>實作<xref:System.Windows.Controls.Expander>控制項。</span><span class="sxs-lookup"><span data-stu-id="a21dd-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="a21dd-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a21dd-109">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="a21dd-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="a21dd-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="a21dd-111">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="a21dd-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="a21dd-112">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="a21dd-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
