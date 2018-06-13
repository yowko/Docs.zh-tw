---
title: 如何：變更 ListView 中資料行的水平對齊
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 31ee131e1cbd6e56ce5b0c29085c2d29e65dc40b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553893"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a><span data-ttu-id="42252-102">如何：變更 ListView 中資料行的水平對齊</span><span class="sxs-lookup"><span data-stu-id="42252-102">How to: Change the Horizontal Alignment of a Column in a ListView</span></span>
<span data-ttu-id="42252-103">根據預設，在每個資料行的內容<xref:System.Windows.Controls.ListViewItem>靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="42252-103">By default, the content of each column in a <xref:System.Windows.Controls.ListViewItem> is left-aligned.</span></span> <span data-ttu-id="42252-104">您可以變更每個資料行的對齊方式，藉由提供<xref:System.Windows.DataTemplate>和設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>內項目的屬性<xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="42252-104">You can change the alignment of each column by providing a <xref:System.Windows.DataTemplate> and setting the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property on the element within the <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="42252-105">本主題說明如何<xref:System.Windows.Controls.ListView>其內容的預設值，以及如何變更的一個資料行的對齊方式對齊<xref:System.Windows.Controls.ListView>。</span><span class="sxs-lookup"><span data-stu-id="42252-105">This topic shows how a <xref:System.Windows.Controls.ListView> aligns its content by default and how to change the alignment of one column in a <xref:System.Windows.Controls.ListView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42252-106">範例</span><span class="sxs-lookup"><span data-stu-id="42252-106">Example</span></span>  
 <span data-ttu-id="42252-107">在下列範例中的資料`Title`和`ISBN`資料行是靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="42252-107">In the following example, the data in the `Title` and `ISBN` columns is left-aligned.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="42252-108">若要變更對齊方式`ISBN`資料行中，您需要指定<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>每個屬性<xref:System.Windows.Controls.ListViewItem>是<xref:System.Windows.HorizontalAlignment.Stretch>，以便在每個項目<xref:System.Windows.Controls.ListViewItem>可以跨越或放置沿著每個資料行的整個寬度。</span><span class="sxs-lookup"><span data-stu-id="42252-108">To change the alignment of the `ISBN` column, you need to specify that the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> property of each <xref:System.Windows.Controls.ListViewItem> is <xref:System.Windows.HorizontalAlignment.Stretch>, so that the elements in each <xref:System.Windows.Controls.ListViewItem> can span or be positioned along the entire width of each column.</span></span> <span data-ttu-id="42252-109">因為<xref:System.Windows.Controls.ListView>繫結至資料來源，您需要建立設定的樣式<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>。</span><span class="sxs-lookup"><span data-stu-id="42252-109">Because the <xref:System.Windows.Controls.ListView> is bound to a data source, you need to create a style that sets the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>.</span></span> <span data-ttu-id="42252-110">接下來，您必須使用<xref:System.Windows.DataTemplate>顯示內容，而不是使用<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="42252-110">Next, you need to use a <xref:System.Windows.DataTemplate> to display the content instead of using the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property.</span></span> <span data-ttu-id="42252-111">若要顯示`ISBN`的每個範本，<xref:System.Windows.DataTemplate>只可包含<xref:System.Windows.Controls.TextBlock>具有其<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性設定為<xref:System.Windows.HorizontalAlignment.Right>。</span><span class="sxs-lookup"><span data-stu-id="42252-111">To display the `ISBN` of each template, the <xref:System.Windows.DataTemplate> can just contain a <xref:System.Windows.Controls.TextBlock> that has its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property set to <xref:System.Windows.HorizontalAlignment.Right>.</span></span>  
  
 <span data-ttu-id="42252-112">下列範例定義的樣式和<xref:System.Windows.DataTemplate>需要製作`ISBN`靠右對齊的資料行並變更<xref:System.Windows.Controls.GridViewColumn>參考<xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="42252-112">The following example defines the style and <xref:System.Windows.DataTemplate> necessary to make the `ISBN` column right-aligned, and changes the <xref:System.Windows.Controls.GridViewColumn> to reference the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="42252-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42252-113">See Also</span></span>  
 [<span data-ttu-id="42252-114">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="42252-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="42252-115">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="42252-115">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="42252-116">使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="42252-116">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="42252-117">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="42252-117">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
