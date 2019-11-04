---
title: 如何：變更 ListView 中資料行的水平對齊
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 5447f1a73b008b2ed4f345eba00f4d631e11e257
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458600"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a><span data-ttu-id="e0e27-102">如何：變更 ListView 中資料行的水平對齊</span><span class="sxs-lookup"><span data-stu-id="e0e27-102">How to: Change the Horizontal Alignment of a Column in a ListView</span></span>
<span data-ttu-id="e0e27-103">根據預設，<xref:System.Windows.Controls.ListViewItem> 中每個資料行的內容都會靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="e0e27-103">By default, the content of each column in a <xref:System.Windows.Controls.ListViewItem> is left-aligned.</span></span> <span data-ttu-id="e0e27-104">您可以藉由提供 <xref:System.Windows.DataTemplate> 並在 <xref:System.Windows.DataTemplate>內的專案上設定 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性，來變更每個資料行的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="e0e27-104">You can change the alignment of each column by providing a <xref:System.Windows.DataTemplate> and setting the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property on the element within the <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="e0e27-105">本主題說明 <xref:System.Windows.Controls.ListView> 預設如何對齊其內容，以及如何變更 <xref:System.Windows.Controls.ListView>中某個資料行的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="e0e27-105">This topic shows how a <xref:System.Windows.Controls.ListView> aligns its content by default and how to change the alignment of one column in a <xref:System.Windows.Controls.ListView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0e27-106">範例</span><span class="sxs-lookup"><span data-stu-id="e0e27-106">Example</span></span>  
 <span data-ttu-id="e0e27-107">在下列範例中，[`Title`] 和 [`ISBN`] 資料行中的資料是靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="e0e27-107">In the following example, the data in the `Title` and `ISBN` columns is left-aligned.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="e0e27-108">若要變更 `ISBN` 資料行的對齊，您必須指定每個 <xref:System.Windows.Controls.ListViewItem> 的 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 屬性 <xref:System.Windows.HorizontalAlignment.Stretch>，以便每個 <xref:System.Windows.Controls.ListViewItem> 中的專案可以橫跨或定位於每個資料行的整個寬度。</span><span class="sxs-lookup"><span data-stu-id="e0e27-108">To change the alignment of the `ISBN` column, you need to specify that the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> property of each <xref:System.Windows.Controls.ListViewItem> is <xref:System.Windows.HorizontalAlignment.Stretch>, so that the elements in each <xref:System.Windows.Controls.ListViewItem> can span or be positioned along the entire width of each column.</span></span> <span data-ttu-id="e0e27-109">因為 <xref:System.Windows.Controls.ListView> 系結至資料來源，所以您必須建立設定 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>的樣式。</span><span class="sxs-lookup"><span data-stu-id="e0e27-109">Because the <xref:System.Windows.Controls.ListView> is bound to a data source, you need to create a style that sets the <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>.</span></span> <span data-ttu-id="e0e27-110">接下來，您必須使用 <xref:System.Windows.DataTemplate> 來顯示內容，而不是使用 [<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>] 屬性。</span><span class="sxs-lookup"><span data-stu-id="e0e27-110">Next, you need to use a <xref:System.Windows.DataTemplate> to display the content instead of using the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property.</span></span> <span data-ttu-id="e0e27-111">若要顯示每個範本的 `ISBN`，<xref:System.Windows.DataTemplate> 只可以包含將其 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性設定為 <xref:System.Windows.HorizontalAlignment.Right>的 <xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="e0e27-111">To display the `ISBN` of each template, the <xref:System.Windows.DataTemplate> can just contain a <xref:System.Windows.Controls.TextBlock> that has its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property set to <xref:System.Windows.HorizontalAlignment.Right>.</span></span>  
  
 <span data-ttu-id="e0e27-112">下列範例會定義使 `ISBN` 資料行靠右對齊所需的樣式和 <xref:System.Windows.DataTemplate>，並將 <xref:System.Windows.Controls.GridViewColumn> 變更為參考 <xref:System.Windows.DataTemplate>。</span><span class="sxs-lookup"><span data-stu-id="e0e27-112">The following example defines the style and <xref:System.Windows.DataTemplate> necessary to make the `ISBN` column right-aligned, and changes the <xref:System.Windows.Controls.GridViewColumn> to reference the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e0e27-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0e27-113">See also</span></span>

- [<span data-ttu-id="e0e27-114">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="e0e27-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="e0e27-115">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="e0e27-115">Data Templating Overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="e0e27-116">使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="e0e27-116">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="e0e27-117">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="e0e27-117">ListView Overview</span></span>](listview-overview.md)
