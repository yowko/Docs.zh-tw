---
title: 如何：處理 ListView 中每個項目的 MouseDoubleClick 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646104"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="8e3a1-102">如何：處理 ListView 中每個項目的 MouseDoubleClick 事件</span><span class="sxs-lookup"><span data-stu-id="8e3a1-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="8e3a1-103">要處理 中的項的<xref:System.Windows.Controls.ListView>事件 ,需要<xref:System.Windows.Controls.ListViewItem>向每個 添加事件處理程式。</span><span class="sxs-lookup"><span data-stu-id="8e3a1-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="8e3a1-104"><xref:System.Windows.Controls.ListView>當 綁定到資料源時,不會顯式創建<xref:System.Windows.Controls.ListViewItem>, 但<xref:System.Windows.EventSetter>可以通過<xref:System.Windows.Controls.ListViewItem>將項添加到 的樣式來處理每個項的事件。</span><span class="sxs-lookup"><span data-stu-id="8e3a1-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e3a1-105">範例</span><span class="sxs-lookup"><span data-stu-id="8e3a1-105">Example</span></span>  
 <span data-ttu-id="8e3a1-106">下面的範例創建一個資料綁定<xref:System.Windows.Controls.ListView>,並<xref:System.Windows.Style>創建一個來向<xref:System.Windows.Controls.ListViewItem>每個添加事件處理程式。</span><span class="sxs-lookup"><span data-stu-id="8e3a1-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="8e3a1-107">下面的示例處理該<xref:System.Windows.Controls.Control.MouseDoubleClick>事件。</span><span class="sxs-lookup"><span data-stu-id="8e3a1-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="8e3a1-108">儘管<xref:System.Windows.Controls.ListView>將繫結為資料來源是最常見的,但可以使用樣式將事件處理程式加入到非資料繫<xref:System.Windows.Controls.ListViewItem><xref:System.Windows.Controls.ListView>結的物件,而不管是否顯式建立<xref:System.Windows.Controls.ListViewItem>。</span><span class="sxs-lookup"><span data-stu-id="8e3a1-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="8e3a1-109">有關顯式和隱式創建的<xref:System.Windows.Controls.ListViewItem>控制件的詳細資訊,請參閱<xref:System.Windows.Controls.ItemsControl>。</span><span class="sxs-lookup"><span data-stu-id="8e3a1-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3a1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e3a1-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="8e3a1-111">資料繫結概述</span><span class="sxs-lookup"><span data-stu-id="8e3a1-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="8e3a1-112">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="8e3a1-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="8e3a1-113">使用 XML 資料提供者與 XPath 查詢繫結到 XML 資料</span><span class="sxs-lookup"><span data-stu-id="8e3a1-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="8e3a1-114">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="8e3a1-114">ListView Overview</span></span>](listview-overview.md)
