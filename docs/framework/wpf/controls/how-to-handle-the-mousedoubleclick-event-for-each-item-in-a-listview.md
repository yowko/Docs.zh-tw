---
title: 如何：處理 ListView 中每個項目的 MouseDoubleClick 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: f9a1e91051a7f86bf78cb08a3d58e57541ae4987
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553843"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="3c6f6-102">如何：處理 ListView 中每個項目的 MouseDoubleClick 事件</span><span class="sxs-lookup"><span data-stu-id="3c6f6-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="3c6f6-103">若要處理的事件中的項目<xref:System.Windows.Controls.ListView>，您需要加入至每個事件處理常式<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="3c6f6-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="3c6f6-104">當<xref:System.Windows.Controls.ListView>繫結至資料來源，您無法明確建立<xref:System.Windows.Controls.ListViewItem>，但您可以藉由新增處理每個項目的事件<xref:System.Windows.EventSetter>風格的<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="3c6f6-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c6f6-105">範例</span><span class="sxs-lookup"><span data-stu-id="3c6f6-105">Example</span></span>  
 <span data-ttu-id="3c6f6-106">下列範例會建立資料繫結<xref:System.Windows.Controls.ListView>並建立<xref:System.Windows.Style>將事件處理常式新增至每個<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="3c6f6-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="3c6f6-107">下列範例會處理<xref:System.Windows.Controls.Control.MouseDoubleClick>事件。</span><span class="sxs-lookup"><span data-stu-id="3c6f6-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="3c6f6-108">雖然它是最常見的繫結<xref:System.Windows.Controls.ListView>到資料來源，您可以使用的樣式，將事件處理常式新增至每個<xref:System.Windows.Controls.ListViewItem>非-資料繫結中<xref:System.Windows.Controls.ListView>不論您是否明確建立<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="3c6f6-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="3c6f6-109">如需有關明確和隱含方式建立<xref:System.Windows.Controls.ListViewItem>控制項，請參閱<xref:System.Windows.Controls.ItemsControl>。</span><span class="sxs-lookup"><span data-stu-id="3c6f6-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6f6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c6f6-110">See Also</span></span>  
 <xref:System.Xml.XmlElement>  
 [<span data-ttu-id="3c6f6-111">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="3c6f6-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="3c6f6-112">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="3c6f6-112">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3c6f6-113">使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="3c6f6-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="3c6f6-114">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="3c6f6-114">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
