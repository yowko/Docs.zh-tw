---
title: TextElement 內容模型概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: acd67dd870c6912eddc368bf674804d98dba2db8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740765"
---
# <a name="textelement-content-model-overview"></a>TextElement 內容模型概觀
此內容模型總覽說明 <xref:System.Windows.Documents.TextElement>支援的內容。 <xref:System.Windows.Documents.Paragraph> 類別是一種 <xref:System.Windows.Documents.TextElement>類型。 內容模型描述哪些物件/元素可包含於其他物件/元素內。 此總覽摘要說明衍生自 <xref:System.Windows.Documents.TextElement>之物件所使用的內容模型。 如需詳細資訊，請參閱非固定格式[檔總覽](flow-document-overview.md)。  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>內容模型圖表  
 下圖摘要說明衍生自 <xref:System.Windows.Documents.TextElement> 之類別的內容模型，以及其他非 `TextElement` 類別如何融入此模型中。  
  
 ![圖表：流程內容內含專案架構](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 如同您在上圖中所見，元素所允許的子系不一定是由類別衍生自 <xref:System.Windows.Documents.Block> 類別還是 <xref:System.Windows.Documents.Inline> 類別所決定。 例如，<xref:System.Windows.Documents.Span> （<xref:System.Windows.Documents.Inline>衍生類別）只能有 <xref:System.Windows.Documents.Inline> 的子專案，但 <xref:System.Windows.Documents.Figure> （也是 <xref:System.Windows.Documents.Inline>衍生的類別）只能有 <xref:System.Windows.Documents.Block> 的子項目。 因此，可快速判斷哪個元素可包含於其他元素中的圖表就很有用。 例如，讓我們使用圖表來決定如何建立 <xref:System.Windows.Controls.RichTextBox>的流程內容。  
  
1. <xref:System.Windows.Controls.RichTextBox> 必須包含 <xref:System.Windows.Documents.FlowDocument>，而後者必須包含 <xref:System.Windows.Documents.Block>衍生的物件。 以下是上圖的對應區段。  
  
     ![圖表： RichTextBox 內含專案規則](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     這是標記目前可能的樣子。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. 根據圖表，有數個 <xref:System.Windows.Documents.Block> 元素可供選擇，包括 <xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.Table>、<xref:System.Windows.Documents.List>和 <xref:System.Windows.Documents.BlockUIContainer> （請參閱上圖中的區塊衍生類別）。 假設我們想要 <xref:System.Windows.Documents.Table>。 根據上圖，<xref:System.Windows.Documents.Table> 包含包含 <xref:System.Windows.Documents.TableRow> 元素的 <xref:System.Windows.Documents.TableRowGroup>，其中包含包含 <xref:System.Windows.Documents.Block>衍生物件的 <xref:System.Windows.Documents.TableCell> 元素。 以下是從上圖取得之 <xref:System.Windows.Documents.Table> 的對應區段。  
  
     ![圖表：資料表&#47;的父子式架構](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     以下是對應的標記。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. 同樣地，<xref:System.Windows.Documents.TableCell>下需要一或多個 <xref:System.Windows.Documents.Block> 元素。 為求簡便，我們在儲存格中放入一些文字。 我們可以使用具有 <xref:System.Windows.Documents.Run> 元素的 <xref:System.Windows.Documents.Paragraph> 來執行這項操作。 以下是圖表中對應的區段，顯示 <xref:System.Windows.Documents.Paragraph> 可以接受 <xref:System.Windows.Documents.Inline> 元素，而且 <xref:System.Windows.Documents.Run> （<xref:System.Windows.Documents.Inline> 專案）只能採用純文字。  
  
     ![圖表：段落&#47;的父子式架構](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![圖表：執行&#47;的父子式架構](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 以下是標記的完整範例。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>以程式設計方式使用 TextElement 內容  
 <xref:System.Windows.Documents.TextElement> 的內容是由集合所組成，因此以程式設計方式操作 <xref:System.Windows.Documents.TextElement> 物件的內容是藉由使用這些集合來完成。 <xref:System.Windows.Documents.TextElement> 衍生的類別使用三種不同的集合：  
  
- <xref:System.Windows.Documents.InlineCollection>：表示 <xref:System.Windows.Documents.Inline> 元素的集合。 <xref:System.Windows.Documents.InlineCollection> 會定義 <xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Span> 和 <xref:System.Windows.Controls.TextBlock> 項目的可允許子內容。  
  
- <xref:System.Windows.Documents.BlockCollection>：表示 <xref:System.Windows.Documents.Block> 元素的集合。 <xref:System.Windows.Documents.BlockCollection> 會定義 <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.ListItem>、<xref:System.Windows.Documents.TableCell>、<xref:System.Windows.Documents.Floater> 和 <xref:System.Windows.Documents.Figure> 項目的可允許子內容。  
  
- <xref:System.Windows.Documents.ListItemCollection>：代表已排序或未排序 <xref:System.Windows.Documents.List>中特定內容專案的流動內容元素。  
  
 您可以使用**內嵌**、**區塊**和**ListItems**的個別屬性，從這些集合操作（新增或移除專案）。 下列範例示範如何使用**內嵌**屬性來操作 Span 的內容。  
  
> [!NOTE]
> 表格會使用數個集合來管理它的內容，但不會在此處加以討論。 如需詳細資訊，請參閱[資料表總覽](table-overview.md)。  
  
 下列範例會建立新的 <xref:System.Windows.Documents.Span> 物件，然後使用 `Add` 方法來新增兩個文字執行，做為 <xref:System.Windows.Documents.Span>的內容子系。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 下列範例會建立新的 <xref:System.Windows.Documents.Run> 元素，並將它插入 <xref:System.Windows.Documents.Span>開頭。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 下列範例會刪除 <xref:System.Windows.Documents.Span>中的最後一個 <xref:System.Windows.Documents.Inline> 元素。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 下列範例會從 <xref:System.Windows.Documents.Span>中清除所有內容（<xref:System.Windows.Documents.Inline> 元素）。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>共用此內容模型的類型  
 下列類型會繼承自 <xref:System.Windows.Documents.TextElement> 類別，而且可用來顯示此總覽中所述的內容。  
  
 <xref:System.Windows.Documents.Bold>、<xref:System.Windows.Documents.Figure>、<xref:System.Windows.Documents.Floater>、<xref:System.Windows.Documents.Hyperlink>、<xref:System.Windows.Documents.InlineUIContainer>、<xref:System.Windows.Documents.Italic>、<xref:System.Windows.Documents.LineBreak>、<xref:System.Windows.Documents.List>、<xref:System.Windows.Documents.ListItem>、<xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Run>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.Span>、<xref:System.Windows.Documents.Table>、<xref:System.Windows.Documents.Underline>。  
  
 請注意，這份清單只包含隨 Windows SDK 散發的非抽象類別型。 您可以使用繼承自 <xref:System.Windows.Documents.TextElement>的其他類型。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>可包含 TextElement 物件的類型  
 請參閱[WPF 內容模型](../controls/wpf-content-model.md)。  
  
## <a name="see-also"></a>請參閱

- [透過 Blocks 屬性管理 FlowDocument](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [透過 Blocks 屬性管理非固定格式內容元素](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [透過 Blocks 屬性管理 FlowDocument](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [透過 Columns 屬性管理表格的資料行](how-to-manipulate-table-columns-through-the-columns-property.md)
- [透過 RowGroups 屬性管理表格的資料列群組](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
