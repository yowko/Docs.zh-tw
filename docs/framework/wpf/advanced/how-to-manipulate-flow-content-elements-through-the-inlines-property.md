---
title: HOW TO：透過 Inlines 屬性管理動態內容項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], manipulating through Inlines property
- documents [WPF], manipulating flow Content elements through Inlines property
- Inlines property [WPF], manipulating flow Content elements
- properties [WPF], Inlines [WPF], manipulating flow Content elements
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
ms.openlocfilehash: cfff958bb4c87e6bfecf2d280224cda233c31806
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942840"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a><span data-ttu-id="7a867-102">HOW TO：透過 Inlines 屬性管理動態內容項目</span><span class="sxs-lookup"><span data-stu-id="7a867-102">How to: Manipulate Flow Content Elements through the Inlines Property</span></span>
<span data-ttu-id="7a867-103">這些範例會展示一些較常見的作業可以在內嵌非固定格式內容項目上執行 (和容器的這類項目，例如<xref:System.Windows.Controls.TextBlock>) 透過**Inlines**屬性。</span><span class="sxs-lookup"><span data-stu-id="7a867-103">These examples demonstrate some of the more common operations that can be performed on inline flow content elements (and containers of such elements, such as <xref:System.Windows.Controls.TextBlock>) through the **Inlines** property.</span></span> <span data-ttu-id="7a867-104">這個屬性用來新增和移除項目從<xref:System.Windows.Documents.InlineCollection>。</span><span class="sxs-lookup"><span data-stu-id="7a867-104">This property is used to add and remove items from <xref:System.Windows.Documents.InlineCollection>.</span></span> <span data-ttu-id="7a867-105">非固定格式內容項目該功能**Inlines**屬性包括：</span><span class="sxs-lookup"><span data-stu-id="7a867-105">Flow content elements that feature an **Inlines** property include:</span></span>  
  
- <xref:System.Windows.Documents.Bold>  
  
- <xref:System.Windows.Documents.Hyperlink>  
  
- <xref:System.Windows.Documents.Italic>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Span>  
  
- <xref:System.Windows.Documents.Underline>  
  
 <span data-ttu-id="7a867-106">若要使用的這些範例中會發生<xref:System.Windows.Documents.Span>與流程內容的項目，但這些技術都適用於所有的項目或裝載的控制項<xref:System.Windows.Documents.InlineCollection>集合。</span><span class="sxs-lookup"><span data-stu-id="7a867-106">These examples happen to use <xref:System.Windows.Documents.Span> as the flow content element, but these techniques are applicable to all elements or controls that host an <xref:System.Windows.Documents.InlineCollection> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a867-107">範例</span><span class="sxs-lookup"><span data-stu-id="7a867-107">Example</span></span>  
 <span data-ttu-id="7a867-108">下列範例會建立新<xref:System.Windows.Documents.Span>物件，然後使用**新增**方法，以新增兩個文字執行為內容的子系<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="7a867-108">The following example creates a new <xref:System.Windows.Documents.Span> object, and then uses the **Add** method to add two text runs as content children of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a><span data-ttu-id="7a867-109">範例</span><span class="sxs-lookup"><span data-stu-id="7a867-109">Example</span></span>  
 <span data-ttu-id="7a867-110">下列範例會建立新<xref:System.Windows.Documents.Run>項目，並將它插入開頭<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="7a867-110">The following example creates a new <xref:System.Windows.Documents.Run> element and inserts it at the beginning of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a><span data-ttu-id="7a867-111">範例</span><span class="sxs-lookup"><span data-stu-id="7a867-111">Example</span></span>  
 <span data-ttu-id="7a867-112">下列範例會取得最上層的數目<xref:System.Windows.Documents.Inline>中所包含的項目<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="7a867-112">The following example gets the number of top-level <xref:System.Windows.Documents.Inline> elements contained in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a><span data-ttu-id="7a867-113">範例</span><span class="sxs-lookup"><span data-stu-id="7a867-113">Example</span></span>  
 <span data-ttu-id="7a867-114">下列範例會刪除最後一個<xref:System.Windows.Documents.Inline>中的項目<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="7a867-114">The following example deletes the last <xref:System.Windows.Documents.Inline> element in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a><span data-ttu-id="7a867-115">範例</span><span class="sxs-lookup"><span data-stu-id="7a867-115">Example</span></span>  
 <span data-ttu-id="7a867-116">下列範例會清除所有內容 (<xref:System.Windows.Documents.Inline>項目) 從<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="7a867-116">The following example clears all of the contents (<xref:System.Windows.Documents.Inline> elements) from the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a><span data-ttu-id="7a867-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a867-117">See also</span></span>

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [<span data-ttu-id="7a867-118">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="7a867-118">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="7a867-119">透過 Blocks 屬性管理 FlowDocument</span><span class="sxs-lookup"><span data-stu-id="7a867-119">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="7a867-120">透過 Columns 屬性管理表格的資料行</span><span class="sxs-lookup"><span data-stu-id="7a867-120">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="7a867-121">透過 RowGroups 屬性管理表格的資料列群組</span><span class="sxs-lookup"><span data-stu-id="7a867-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
