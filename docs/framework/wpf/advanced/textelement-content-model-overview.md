---
title: "TextElement 內容模型概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81f95ea4582230fe66c59655ab9b98a405c1e173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="textelement-content-model-overview"></a><span data-ttu-id="b055d-102">TextElement 內容模型概觀</span><span class="sxs-lookup"><span data-stu-id="b055d-102">TextElement Content Model Overview</span></span>
<span data-ttu-id="b055d-103">本內容模型的概觀說明支援的內容<xref:System.Windows.Documents.TextElement>。</span><span class="sxs-lookup"><span data-stu-id="b055d-103">This content model overview describes the supported content for a <xref:System.Windows.Documents.TextElement>.</span></span> <span data-ttu-id="b055d-104"><xref:System.Windows.Documents.Paragraph>類別是一種<xref:System.Windows.Documents.TextElement>。</span><span class="sxs-lookup"><span data-stu-id="b055d-104">The <xref:System.Windows.Documents.Paragraph> class is a type of <xref:System.Windows.Documents.TextElement>.</span></span> <span data-ttu-id="b055d-105">內容模型描述哪些物件/元素可包含於其他物件/元素內。</span><span class="sxs-lookup"><span data-stu-id="b055d-105">A content model describes what objects/elements can be contained in others.</span></span> <span data-ttu-id="b055d-106">本概觀摘要說明用於衍生自物件的內容模型<xref:System.Windows.Documents.TextElement>。</span><span class="sxs-lookup"><span data-stu-id="b055d-106">This overview summarizes the content model used for objects derived from <xref:System.Windows.Documents.TextElement>.</span></span> <span data-ttu-id="b055d-107">如需詳細資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b055d-107">For more information, see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md).</span></span>  
  
  
<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a><span data-ttu-id="b055d-108">內容模型圖表</span><span class="sxs-lookup"><span data-stu-id="b055d-108">Content Model Diagram</span></span>  
 <span data-ttu-id="b055d-109">下圖摘要說明內容的模型類別衍生自<xref:System.Windows.Documents.TextElement>以及如何其他非`TextElement`符合此模型的類別。</span><span class="sxs-lookup"><span data-stu-id="b055d-109">The following diagram summarizes the content model for classes derived from <xref:System.Windows.Documents.TextElement> as well as how other non- `TextElement` classes fit into this model.</span></span>  
  
 <span data-ttu-id="b055d-110">![圖表：非固定格式內容內含項目結構描述](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")</span><span class="sxs-lookup"><span data-stu-id="b055d-110">![Diagram: Flow content containment schema](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")</span></span>  
  
 <span data-ttu-id="b055d-111">可以從上圖看出，允許的項目子系不一定是取決於是否的類別衍生自<xref:System.Windows.Documents.Block>類別或<xref:System.Windows.Documents.Inline>類別。</span><span class="sxs-lookup"><span data-stu-id="b055d-111">As can be seen from the preceding diagram, the children allowed for an element are not necessarily determined by whether a class is derived from the <xref:System.Windows.Documents.Block> class or an <xref:System.Windows.Documents.Inline> class.</span></span> <span data-ttu-id="b055d-112">例如， <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline>-衍生的類別) 只能有<xref:System.Windows.Documents.Inline>子項目，但<xref:System.Windows.Documents.Figure>(也<xref:System.Windows.Documents.Inline>-衍生的類別) 只能有<xref:System.Windows.Documents.Block>子項目。</span><span class="sxs-lookup"><span data-stu-id="b055d-112">For example, a <xref:System.Windows.Documents.Span> (an <xref:System.Windows.Documents.Inline>-derived class) can only have <xref:System.Windows.Documents.Inline> child elements, but a <xref:System.Windows.Documents.Figure> (also an <xref:System.Windows.Documents.Inline>-derived class) can only have <xref:System.Windows.Documents.Block> child elements.</span></span> <span data-ttu-id="b055d-113">因此，可快速判斷哪個元素可包含於其他元素中的圖表就很有用。</span><span class="sxs-lookup"><span data-stu-id="b055d-113">Therefore, a diagram is useful for quickly determining what element can be contained in another.</span></span> <span data-ttu-id="b055d-114">例如，讓我們使用圖表，即可決定如何建構的非固定格式內容<xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="b055d-114">As an example, let's use the diagram to determine how to construct the flow content of a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
1.  <span data-ttu-id="b055d-115">A<xref:System.Windows.Controls.RichTextBox>必須包含<xref:System.Windows.Documents.FlowDocument>其中必須包含<xref:System.Windows.Documents.Block>-衍生物件。</span><span class="sxs-lookup"><span data-stu-id="b055d-115">A <xref:System.Windows.Controls.RichTextBox> must contain a <xref:System.Windows.Documents.FlowDocument> which in turn must contain a <xref:System.Windows.Documents.Block>-derived object.</span></span> <span data-ttu-id="b055d-116">以下是上圖的對應區段。</span><span class="sxs-lookup"><span data-stu-id="b055d-116">The following is the corresponding segment from the preceding diagram.</span></span>  
  
     <span data-ttu-id="b055d-117">![圖表：RichTextBox 內含項目規則](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")</span><span class="sxs-lookup"><span data-stu-id="b055d-117">![Diagram: RichTextBox containment rules](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")</span></span>  
  
     <span data-ttu-id="b055d-118">這是標記目前可能的樣子。</span><span class="sxs-lookup"><span data-stu-id="b055d-118">Thus far, this is what the markup might look like.</span></span>  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  <span data-ttu-id="b055d-119">根據圖表中，有好幾種<xref:System.Windows.Documents.Block>包括從選擇的項目<xref:System.Windows.Documents.Paragraph>， <xref:System.Windows.Documents.Section>， <xref:System.Windows.Documents.Table>， <xref:System.Windows.Documents.List>，和<xref:System.Windows.Documents.BlockUIContainer>（請參閱區塊所衍生的類別，在上圖）。</span><span class="sxs-lookup"><span data-stu-id="b055d-119">According to the diagram, there are several <xref:System.Windows.Documents.Block> elements to choose from including <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, and <xref:System.Windows.Documents.BlockUIContainer> (see Block-derived classes in the preceding diagram).</span></span> <span data-ttu-id="b055d-120">假設我們想要<xref:System.Windows.Documents.Table>。</span><span class="sxs-lookup"><span data-stu-id="b055d-120">Let's say we want a <xref:System.Windows.Documents.Table>.</span></span> <span data-ttu-id="b055d-121">上圖中，根據<xref:System.Windows.Documents.Table>包含<xref:System.Windows.Documents.TableRowGroup>包含<xref:System.Windows.Documents.TableRow>項目，其中包含<xref:System.Windows.Documents.TableCell>項目，其中包含<xref:System.Windows.Documents.Block>-衍生物件。</span><span class="sxs-lookup"><span data-stu-id="b055d-121">According to the preceding diagram, a <xref:System.Windows.Documents.Table> contains a <xref:System.Windows.Documents.TableRowGroup> containing <xref:System.Windows.Documents.TableRow> elements, which contain <xref:System.Windows.Documents.TableCell> elements which contain a <xref:System.Windows.Documents.Block>-derived object.</span></span> <span data-ttu-id="b055d-122">以下是對應的區段，如<xref:System.Windows.Documents.Table>取自先前的圖表。</span><span class="sxs-lookup"><span data-stu-id="b055d-122">The following is the corresponding segment for <xref:System.Windows.Documents.Table> taken from the preceding diagram.</span></span>  
  
     <span data-ttu-id="b055d-123">![圖表︰表格的父/子結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")</span><span class="sxs-lookup"><span data-stu-id="b055d-123">![Diagram: Parent&#47;child schema for Table](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")</span></span>  
  
     <span data-ttu-id="b055d-124">以下是對應的標記。</span><span class="sxs-lookup"><span data-stu-id="b055d-124">The following is the corresponding markup.</span></span>  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  <span data-ttu-id="b055d-125">同樣地，一或多個<xref:System.Windows.Documents.Block>都需要項目下方<xref:System.Windows.Documents.TableCell>。</span><span class="sxs-lookup"><span data-stu-id="b055d-125">Again, one or more <xref:System.Windows.Documents.Block> elements are required underneath a <xref:System.Windows.Documents.TableCell>.</span></span> <span data-ttu-id="b055d-126">為求簡便，我們在儲存格中放入一些文字。</span><span class="sxs-lookup"><span data-stu-id="b055d-126">To make it simple, let's place some text inside the cell.</span></span> <span data-ttu-id="b055d-127">我們可以這樣使用<xref:System.Windows.Documents.Paragraph>與<xref:System.Windows.Documents.Run>項目。</span><span class="sxs-lookup"><span data-stu-id="b055d-127">We can do this using a <xref:System.Windows.Documents.Paragraph> with a <xref:System.Windows.Documents.Run> element.</span></span> <span data-ttu-id="b055d-128">以下是從圖表中顯示的對應區段<xref:System.Windows.Documents.Paragraph>可以採取<xref:System.Windows.Documents.Inline>項目， <xref:System.Windows.Documents.Run> (<xref:System.Windows.Documents.Inline>項目) 可能只需要純文字。</span><span class="sxs-lookup"><span data-stu-id="b055d-128">The following is the corresponding segments from the diagram showing that a <xref:System.Windows.Documents.Paragraph> can take an <xref:System.Windows.Documents.Inline> element and that a <xref:System.Windows.Documents.Run> (an <xref:System.Windows.Documents.Inline> element) can only take plain text.</span></span>  
  
     <span data-ttu-id="b055d-129">![圖表︰段落的父/子結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")</span><span class="sxs-lookup"><span data-stu-id="b055d-129">![Diagram: Parent&#47;child schema for Paragraph](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")</span></span>  
  
     <span data-ttu-id="b055d-130">![圖表︰回合的父/子結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")</span><span class="sxs-lookup"><span data-stu-id="b055d-130">![Diagram: Parent&#47;Child schema for Run](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")</span></span>  
  
 <span data-ttu-id="b055d-131">以下是標記的完整範例。</span><span class="sxs-lookup"><span data-stu-id="b055d-131">The following is the entire example in markup.</span></span>  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a><span data-ttu-id="b055d-132">以程式設計方式使用 TextElement 內容</span><span class="sxs-lookup"><span data-stu-id="b055d-132">Working with TextElement Content Programmatically</span></span>  
 <span data-ttu-id="b055d-133">內容<xref:System.Windows.Documents.TextElement>所組成的集合，因此以程式設計方式管理的內容<xref:System.Windows.Documents.TextElement>物件由使用這些集合。</span><span class="sxs-lookup"><span data-stu-id="b055d-133">The contents of a <xref:System.Windows.Documents.TextElement> is made up by collections and so programmatically manipulating the contents of <xref:System.Windows.Documents.TextElement> objects is done by working with these collections.</span></span> <span data-ttu-id="b055d-134">有三個不同的集合所使用<xref:System.Windows.Documents.TextElement>-衍生的類別：</span><span class="sxs-lookup"><span data-stu-id="b055d-134">There are three different collections used by <xref:System.Windows.Documents.TextElement> -derived classes:</span></span>  
  
-   <span data-ttu-id="b055d-135"><xref:System.Windows.Documents.InlineCollection>： 表示的集合<xref:System.Windows.Documents.Inline>項目。</span><span class="sxs-lookup"><span data-stu-id="b055d-135"><xref:System.Windows.Documents.InlineCollection>: Represents a collection of <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="b055d-136"><xref:System.Windows.Documents.InlineCollection>定義可允許子內容的<xref:System.Windows.Documents.Paragraph>， <xref:System.Windows.Documents.Span>，和<xref:System.Windows.Controls.TextBlock>項目。</span><span class="sxs-lookup"><span data-stu-id="b055d-136"><xref:System.Windows.Documents.InlineCollection> defines the allowable child content of the <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>, and <xref:System.Windows.Controls.TextBlock> elements.</span></span>  
  
-   <span data-ttu-id="b055d-137"><xref:System.Windows.Documents.BlockCollection>： 表示的集合<xref:System.Windows.Documents.Block>項目。</span><span class="sxs-lookup"><span data-stu-id="b055d-137"><xref:System.Windows.Documents.BlockCollection>: Represents a collection of <xref:System.Windows.Documents.Block> elements.</span></span> <span data-ttu-id="b055d-138"><xref:System.Windows.Documents.BlockCollection>定義可允許子內容的<xref:System.Windows.Documents.FlowDocument>， <xref:System.Windows.Documents.Section>， <xref:System.Windows.Documents.ListItem>， <xref:System.Windows.Documents.TableCell>， <xref:System.Windows.Documents.Floater>，和<xref:System.Windows.Documents.Figure>項目。</span><span class="sxs-lookup"><span data-stu-id="b055d-138"><xref:System.Windows.Documents.BlockCollection> defines the allowable child content of the <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>, and <xref:System.Windows.Documents.Figure> elements.</span></span>  
  
-   <span data-ttu-id="b055d-139"><xref:System.Windows.Documents.ListItemCollection>： 代表特定的內容項目已排序流動內容項目或未排序<xref:System.Windows.Documents.List>。</span><span class="sxs-lookup"><span data-stu-id="b055d-139"><xref:System.Windows.Documents.ListItemCollection>: A flow content element that represents a particular content item in an ordered or unordered <xref:System.Windows.Documents.List>.</span></span>  
  
 <span data-ttu-id="b055d-140">您可以使用操作 （新增或移除項目） 從這些集合使用的個別屬性**內嵌**，**區塊**，和**ListItems**。</span><span class="sxs-lookup"><span data-stu-id="b055d-140">You can manipulate (add or remove items) from these collections using the respective properties of **Inlines**, **Blocks**, and **ListItems**.</span></span> <span data-ttu-id="b055d-141">下列範例示範如何操作的範圍使用內容**內嵌**屬性。</span><span class="sxs-lookup"><span data-stu-id="b055d-141">The following examples show how to manipulate the contents of a Span using the **Inlines** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b055d-142">表格會使用數個集合來管理它的內容，但不會在此處加以討論。</span><span class="sxs-lookup"><span data-stu-id="b055d-142">Table uses several collections to manipulate its contents, but they are not covered here.</span></span> <span data-ttu-id="b055d-143">如需詳細資訊，請參閱[資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b055d-143">For more information, see [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="b055d-144">下列範例會建立新<xref:System.Windows.Documents.Span>物件，然後使用`Add`方法，將兩個文字執行內容的子系<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="b055d-144">The following example creates a new <xref:System.Windows.Documents.Span> object, and then uses the `Add` method to add two text runs as content children of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 <span data-ttu-id="b055d-145">下列範例會建立新<xref:System.Windows.Documents.Run>項目並將它的開頭插入<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="b055d-145">The following example creates a new <xref:System.Windows.Documents.Run> element and inserts it at the beginning of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 <span data-ttu-id="b055d-146">下列範例會刪除最後一個<xref:System.Windows.Documents.Inline>中的項目<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="b055d-146">The following example deletes the last <xref:System.Windows.Documents.Inline> element in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 <span data-ttu-id="b055d-147">下列範例會清除所有內容 (<xref:System.Windows.Documents.Inline>項目) 從<xref:System.Windows.Documents.Span>。</span><span class="sxs-lookup"><span data-stu-id="b055d-147">The following example clears all of the contents (<xref:System.Windows.Documents.Inline> elements) from the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a><span data-ttu-id="b055d-148">共用此內容模型的類型</span><span class="sxs-lookup"><span data-stu-id="b055d-148">Types That Share This Content Model</span></span>  
 <span data-ttu-id="b055d-149">下列類型繼承自<xref:System.Windows.Documents.TextElement>類別，並可用於顯示本概觀中所述的內容。</span><span class="sxs-lookup"><span data-stu-id="b055d-149">The following types inherit from the <xref:System.Windows.Documents.TextElement> class and may be used to display the content described in this overview.</span></span>  
  
 <span data-ttu-id="b055d-150"><xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.</span><span class="sxs-lookup"><span data-stu-id="b055d-150"><xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.</span></span>  
  
 <span data-ttu-id="b055d-151">請注意，此清單只包含隨附的非抽象類型[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b055d-151">Note that this list only includes nonabstract types distributed with the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="b055d-152">您可以使用繼承自其他類型<xref:System.Windows.Documents.TextElement>。</span><span class="sxs-lookup"><span data-stu-id="b055d-152">You may use other types that inherit from <xref:System.Windows.Documents.TextElement>.</span></span>  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a><span data-ttu-id="b055d-153">可包含 TextElement 物件的類型</span><span class="sxs-lookup"><span data-stu-id="b055d-153">Types That Can Contain TextElement Objects</span></span>  
 <span data-ttu-id="b055d-154">請參閱[WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b055d-154">See [WPF Content Model](../../../../docs/framework/wpf/controls/wpf-content-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b055d-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b055d-155">See Also</span></span>  
 [<span data-ttu-id="b055d-156">透過 Blocks 屬性管理 FlowDocument</span><span class="sxs-lookup"><span data-stu-id="b055d-156">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="b055d-157">透過 Blocks 屬性管理非固定格式內容元素</span><span class="sxs-lookup"><span data-stu-id="b055d-157">Manipulate Flow Content Elements through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-flow-content-elements-through-the-blocks-property.md)  
 [<span data-ttu-id="b055d-158">透過 Blocks 屬性管理 FlowDocument</span><span class="sxs-lookup"><span data-stu-id="b055d-158">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="b055d-159">透過 Columns 屬性管理表格的資料行</span><span class="sxs-lookup"><span data-stu-id="b055d-159">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [<span data-ttu-id="b055d-160">透過 RowGroups 屬性管理表格的資料列群組</span><span class="sxs-lookup"><span data-stu-id="b055d-160">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
