---
title: HOW TO：排序檢視中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 50e1426f2a220c7d947f7feb9c3ec7e1c4de7643
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522670"
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="01d37-102">HOW TO：排序檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="01d37-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="01d37-103">這個範例說明如何排序檢視中的資料。</span><span class="sxs-lookup"><span data-stu-id="01d37-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d37-104">範例</span><span class="sxs-lookup"><span data-stu-id="01d37-104">Example</span></span>  
 <span data-ttu-id="01d37-105">下列範例會建立簡易<xref:System.Windows.Controls.ListBox>和<xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="01d37-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="01d37-106"><xref:System.Windows.Controls.Primitives.ButtonBase.Click>  按鈕的事件處理常式包含排序項目中的邏輯<xref:System.Windows.Controls.ListBox>以遞減的順序。</span><span class="sxs-lookup"><span data-stu-id="01d37-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="01d37-107">您可以新增項目，因為<xref:System.Windows.Controls.ListBox>這種方式將它們加入至<xref:System.Windows.Controls.ItemCollection>的<xref:System.Windows.Controls.ListBox>，以及<xref:System.Windows.Controls.ItemCollection>衍生自<xref:System.Windows.Data.CollectionView>類別。</span><span class="sxs-lookup"><span data-stu-id="01d37-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="01d37-108">如果您要繫結您<xref:System.Windows.Controls.ListBox>集合，使用<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性，您可以使用相同的技巧來排序。</span><span class="sxs-lookup"><span data-stu-id="01d37-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="01d37-109">只要您有檢視物件的參考，您可以使用相同的技巧來排序其他集合檢視的內容。</span><span class="sxs-lookup"><span data-stu-id="01d37-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="01d37-110">如需濆爧髍孮檢視的範例，請參閱 <<c0> [ 取得資料集合的預設檢視](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="01d37-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="01d37-111">如需其他範例，請參閱[排序 GridView 資料行時按一下標頭](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。</span><span class="sxs-lookup"><span data-stu-id="01d37-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="01d37-112">如需有關檢視的詳細資訊，請參閱繫結至集合中[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="01d37-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="01d37-113">如需如何將排序邏輯中的範例[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，請參閱 <<c2> [ 排序與群組資料使用 XAML 中的檢視](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="01d37-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d37-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01d37-114">See also</span></span>
- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [<span data-ttu-id="01d37-115">在按一下標頭時排序 GridView 資料行</span><span class="sxs-lookup"><span data-stu-id="01d37-115">Sort a GridView Column When a Header Is Clicked</span></span>](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [<span data-ttu-id="01d37-116">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="01d37-116">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="01d37-117">篩選檢視中的資料</span><span class="sxs-lookup"><span data-stu-id="01d37-117">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="01d37-118">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="01d37-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
