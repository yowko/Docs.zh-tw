---
title: HOW TO：處理 ListView 中每個項目的 MouseDoubleClick 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 443e5c620ef5bf240d3e317f0234aac0b29b456f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145076"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="c1af5-102">HOW TO：處理 ListView 中每個項目的 MouseDoubleClick 事件</span><span class="sxs-lookup"><span data-stu-id="c1af5-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="c1af5-103">若要處理的事件中的項目<xref:System.Windows.Controls.ListView>，您需要將事件處理常式新增至每個<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="c1af5-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="c1af5-104">當<xref:System.Windows.Controls.ListView>繫結至資料來源，您無法明確建立<xref:System.Windows.Controls.ListViewItem>，但您可以藉由新增來處理每個項目的事件<xref:System.Windows.EventSetter>風格的<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="c1af5-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1af5-105">範例</span><span class="sxs-lookup"><span data-stu-id="c1af5-105">Example</span></span>  
 <span data-ttu-id="c1af5-106">下列範例會建立資料繫結<xref:System.Windows.Controls.ListView>，並建立<xref:System.Windows.Style>將事件處理常式新增至每個<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="c1af5-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="c1af5-107">下列範例會處理<xref:System.Windows.Controls.Control.MouseDoubleClick>事件。</span><span class="sxs-lookup"><span data-stu-id="c1af5-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="c1af5-108">雖然它是最常用來繫結<xref:System.Windows.Controls.ListView>到資料來源，您可以將事件處理常式新增至每個使用樣式<xref:System.Windows.Controls.ListViewItem>在非資料-繫結<xref:System.Windows.Controls.ListView>不論您是否明確建立<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="c1af5-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="c1af5-109">如需有關明確和隱含方式建立<xref:System.Windows.Controls.ListViewItem>控制項，請參閱<xref:System.Windows.Controls.ItemsControl>。</span><span class="sxs-lookup"><span data-stu-id="c1af5-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1af5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1af5-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="c1af5-111">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="c1af5-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="c1af5-112">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="c1af5-112">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="c1af5-113">使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="c1af5-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="c1af5-114">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="c1af5-114">ListView Overview</span></span>](listview-overview.md)
