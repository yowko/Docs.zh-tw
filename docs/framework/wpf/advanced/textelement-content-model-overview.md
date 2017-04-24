---
title: "TextElement 內容模型概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文件, 非固定格式文件"
  - "非固定格式內容項目 [WPF], TextElement 內容模型"
  - "非固定格式文件"
  - "TextElement 內容模型"
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# TextElement 內容模型概觀
本內容模型概觀說明 <xref:System.Windows.Documents.TextElement> 支援的內容。  <xref:System.Windows.Documents.Paragraph> 類別屬於 <xref:System.Windows.Documents.TextElement> 型別。  內容模型可說明其他物件\/項目可包含的物件\/項目。  本概觀將摘要說明衍生自 <xref:System.Windows.Documents.TextElement> 的物件所適用的內容模型。  如需詳細資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  
  
   
  
<a name="text_element_classes"></a>   
## 內容模型圖表  
 下圖摘要說明衍生自 <xref:System.Windows.Documents.TextElement> 的類別所適用的內容模型，以及其他可包含在此模型中的非 `TextElement` 類別。  
  
 ![圖表：非固定格式內容內含項目結構描述](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow\_Content\_Schema")  
  
 如上圖所示，某個項目所允許的子系，不一定取決於類別是衍生自 <xref:System.Windows.Documents.Block> 類別還是 <xref:System.Windows.Documents.Inline> 類別。  例如，<xref:System.Windows.Documents.Span> \(<xref:System.Windows.Documents.Inline> 的衍生類別\) 只能具有 <xref:System.Windows.Documents.Inline> 子項目，但 <xref:System.Windows.Documents.Figure> \(也是 <xref:System.Windows.Documents.Inline> 的衍生類別\) 只能具有 <xref:System.Windows.Documents.Block> 子項目。  因此，這張圖表有助於快速判斷某個項目是否可以包含其他項目。  例如，我們將用圖表決定如何建構 <xref:System.Windows.Controls.RichTextBox> 的非固定格式內容。  
  
1.  <xref:System.Windows.Controls.RichTextBox> 必須包含 <xref:System.Windows.Documents.FlowDocument>，而後者必須包含 <xref:System.Windows.Documents.Block> 的衍生物件。  下列是上圖中的對應區段。  
  
     ![圖表：RichTextBox 內含項目規則](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow\_Ovw\_SchemaWalkThrough1")  
  
     因此，標記 \(Markup\) 的外觀可能如下。  
  
     [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  根據圖表，有多種 <xref:System.Windows.Documents.Block> 項目可供選擇，包括 <xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.Table>、<xref:System.Windows.Documents.List> 與 <xref:System.Windows.Documents.BlockUIContainer> \(請參閱上圖的區塊衍生類別\)。  假設我們要用 <xref:System.Windows.Documents.Table>。  根據上圖，<xref:System.Windows.Documents.Table> 含有內含 <xref:System.Windows.Documents.TableRow> 項目的 <xref:System.Windows.Documents.TableRowGroup>，而後者又包含具有 <xref:System.Windows.Documents.Block> 衍生物件的 <xref:System.Windows.Documents.TableCell> 項目。  下列是取自上圖之 <xref:System.Windows.Documents.Table> 的對應區段。  
  
     ![圖表：Table 的父代&#47;子系結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow\_Ovw\_SchemaWalkThrough2")  
  
     下列是對應的標記。  
  
     [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  同樣地，<xref:System.Windows.Documents.TableCell> 下必須要有一個或多個 <xref:System.Windows.Documents.Block> 項目。  為將其簡化，我們將在儲存格中加入一些文字。  我們可以使用 <xref:System.Windows.Documents.Paragraph> 與 <xref:System.Windows.Documents.Run> 項目來執行這個動作。  下列是圖表中的對應區段，其中顯示 <xref:System.Windows.Documents.Paragraph> 可採用 <xref:System.Windows.Documents.Inline> 項目，而 <xref:System.Windows.Documents.Run> \(<xref:System.Windows.Documents.Inline> 項目\) 只能採用純文字。  
  
     ![圖表：Paragraph 的父代&#47;子系結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow\_Ovw\_SchemaWalkThrough3")  
  
     ![圖表：Run 的父代&#47;子系結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow\_Ovw\_SchemaWalkThrough4")  
  
 下列是標記的完整範例。  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## 以程式設計方式使用 TextElement 內容  
 <xref:System.Windows.Documents.TextElement> 的內容由集合所構成，因此 <xref:System.Windows.Documents.TextElement> 物件內容的程式化操作可透過這些集合的使用來完成。  <xref:System.Windows.Documents.TextElement> 的衍生類別可使用三種不同的集合：  
  
-   <xref:System.Windows.Documents.InlineCollection>：表示 <xref:System.Windows.Documents.Inline> 項目的集合。  <xref:System.Windows.Documents.InlineCollection> 會定義 <xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Span> 及 <xref:System.Windows.Controls.TextBlock> 項目的可允許子內容。  
  
-   <xref:System.Windows.Documents.BlockCollection>：表示 <xref:System.Windows.Documents.Block> 項目的集合。  <xref:System.Windows.Documents.BlockCollection> 會定義 <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.ListItem>、<xref:System.Windows.Documents.TableCell>、<xref:System.Windows.Documents.Floater> 及 <xref:System.Windows.Documents.Figure> 項目的可允許子內容。  
  
-   <xref:System.Windows.Documents.ListItemCollection>：在已排序或未排序的 <xref:System.Windows.Documents.List> 中代表特殊內容項目的非固定格式內容項目。  
  
 您可以分別使用 **Inlines**、**Blocks** 與 **ListItems** 等屬性，從這些集合進行操作 \(加入或移除項目\)。  下列範例顯示如何使用 **Inlines** 屬性來操作 Span 的內容。  
  
> [!NOTE]
>  資料表可使用數個集合來操作其內容，但在此不加以說明。  如需詳細資訊，請參閱[資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)。  
  
 下列範例會建立新的 <xref:System.Windows.Documents.Span> 物件，然後使用 `Add` 方法加入兩行文字，做為 <xref:System.Windows.Documents.Span> 的內容子系。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 下列範例會建立新的 <xref:System.Windows.Documents.Run> 項目，並將其插入至 <xref:System.Windows.Documents.Span> 的開頭。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 下列範例會刪除 <xref:System.Windows.Documents.Span> 中的最後一個 <xref:System.Windows.Documents.Inline> 項目。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 下列範例會清除 <xref:System.Windows.Documents.Span> 的所有內容 \(<xref:System.Windows.Documents.Inline> 項目\)。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## 共用此內容模型的型別  
 下列型別繼承自 <xref:System.Windows.Documents.TextElement> 類別，並可用來顯示此概觀所說明的內容。  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 請注意，此清單僅包含 [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] 所散發的非抽象型別。  您可以使用繼承自 <xref:System.Windows.Documents.TextElement> 的其他型別。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## 可包含 TextElement 物件的型別  
 請參閱 [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)。  
  
## 請參閱  
 [透過 Blocks 屬性管理 FlowDocument ](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [透過 Blocks 屬性管理非固定格式內容項目](../../../../docs/framework/wpf/advanced/how-to-manipulate-flow-content-elements-through-the-blocks-property.md)   
 [透過 Blocks 屬性管理 FlowDocument ](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)   
 [透過 Columns 屬性管理資料表的資料行](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)   
 [透過 RowGroups 屬性管理資料表的資料列群組](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)