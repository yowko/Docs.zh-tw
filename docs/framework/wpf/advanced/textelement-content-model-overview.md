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
ms.openlocfilehash: 21df7228f8dca884c5f36be23ae1aced7b31cc9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942209"
---
# <a name="textelement-content-model-overview"></a>TextElement 內容模型概觀
此內容模型總覽描述支援的內容<xref:System.Windows.Documents.TextElement>。 類別是的一<xref:System.Windows.Documents.TextElement>種類型。 <xref:System.Windows.Documents.Paragraph> 內容模型描述哪些物件/元素可包含於其他物件/元素內。 此總覽摘要說明衍生自之<xref:System.Windows.Documents.TextElement>物件所使用的內容模型。 如需詳細資訊, 請參閱非固定格式[檔總覽](flow-document-overview.md)。  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>內容模型圖表  
 下圖摘要說明衍生自之<xref:System.Windows.Documents.TextElement>類別的內容模型, 以及其他`TextElement`非類別如何配合此模型。  
  
 ![空間流程內容內含專案]架構(./media/flow-content-schema.png "Flow_Content_Schema")  
  
 如同您在上圖中所見, 元素所允許的子系不一定是由類別衍生自<xref:System.Windows.Documents.Block>類別<xref:System.Windows.Documents.Inline>或類別所決定。 例如<xref:System.Windows.Documents.Span> , <xref:System.Windows.Documents.Figure> <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Block> (衍生類別) 只能有<xref:System.Windows.Documents.Inline>子專案, 但 (也是衍生類別) 只能有子項目。 <xref:System.Windows.Documents.Inline> 因此，可快速判斷哪個元素可包含於其他元素中的圖表就很有用。 例如, 讓我們使用圖表來決定如何建立的流程內容<xref:System.Windows.Controls.RichTextBox>。  
  
1. 必須包含, 而後者又必須包含<xref:System.Windows.Documents.Block>衍生的物件。 <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.RichTextBox> 以下是上圖的對應區段。  
  
     ![空間RichTextBox 內含專案]規則(./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     這是標記目前可能的樣子。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. 根據圖表, 有<xref:System.Windows.Documents.Block>數個元素可供選擇, 包括<xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.Section>、 <xref:System.Windows.Documents.Table>、 <xref:System.Windows.Documents.List>和<xref:System.Windows.Documents.BlockUIContainer> (請參閱上圖中的區塊衍生類別)。 假設我們想要<xref:System.Windows.Documents.Table>。 根據上圖所<xref:System.Windows.Documents.Table>示, <xref:System.Windows.Documents.TableRowGroup>包含<xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.TableCell> 包含<xref:System.Windows.Documents.Block>元素, 其中包含包含衍生物件的專案。 以下是<xref:System.Windows.Documents.Table>取自上圖的對應區段。  
  
     ![空間&#47;資料表](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")的父子式架構  
  
     以下是對應的標記。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. 同樣地, <xref:System.Windows.Documents.TableCell>底下需要<xref:System.Windows.Documents.Block>一或多個元素。 為求簡便，我們在儲存格中放入一些文字。 我們可以使用<xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run>搭配專案來執行這項操作。 以下是圖表中對應的區段, 其中<xref:System.Windows.Documents.Paragraph>顯示可以<xref:System.Windows.Documents.Inline>接受專案<xref:System.Windows.Documents.Inline> , 而且<xref:System.Windows.Documents.Run> (專案) 只能採用純文字。  
  
     ![空間&#47;段落](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")的父子式架構  
  
     ![空間&#47;執行](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")的父子式架構  
  
 以下是標記的完整範例。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>以程式設計方式使用 TextElement 內容  
 的內容<xref:System.Windows.Documents.TextElement>是由集合所組成, 因此以程式設計方式操作<xref:System.Windows.Documents.TextElement>物件的內容, 是藉由使用這些集合來完成。 衍生類別使用<xref:System.Windows.Documents.TextElement>三種不同的集合:  
  
- <xref:System.Windows.Documents.InlineCollection>：表示 <xref:System.Windows.Documents.Inline> 項目的集合。 <xref:System.Windows.Documents.InlineCollection> 會定義 <xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Span> 和 <xref:System.Windows.Controls.TextBlock> 項目的可允許子內容。  
  
- <xref:System.Windows.Documents.BlockCollection>：表示 <xref:System.Windows.Documents.Block> 項目的集合。 <xref:System.Windows.Documents.BlockCollection> 會定義 <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.ListItem>、<xref:System.Windows.Documents.TableCell>、<xref:System.Windows.Documents.Floater> 和 <xref:System.Windows.Documents.Figure> 項目的可允許子內容。  
  
- <xref:System.Windows.Documents.ListItemCollection>：表示已排序或未排序<xref:System.Windows.Documents.List>之特定內容專案的流動內容元素。  
  
 您可以使用**內嵌**、**區塊**和**ListItems**的個別屬性, 從這些集合操作 (新增或移除專案)。 下列範例示範如何使用**內嵌**屬性來操作 Span 的內容。  
  
> [!NOTE]
> 表格會使用數個集合來管理它的內容，但不會在此處加以討論。 如需詳細資訊, 請參閱[資料表總覽](table-overview.md)。  
  
 下列範例會建立新<xref:System.Windows.Documents.Span>的物件, 然後`Add`使用方法來加入兩個文字執行, 做為的<xref:System.Windows.Documents.Span>內容子系。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 下列範例會建立新<xref:System.Windows.Documents.Run>的專案, 並將其插入的開頭。 <xref:System.Windows.Documents.Span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 下列範例會刪除<xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span>中的最後一個元素。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 下列範例會<xref:System.Windows.Documents.Span>從中清除所有的內容<xref:System.Windows.Documents.Inline> (元素)。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>共用此內容模型的類型  
 下列類型會繼承自<xref:System.Windows.Documents.TextElement>類別, 而且可用來顯示此總覽中所述的內容。  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 請注意, 這份清單只包含與一起散發[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]的非抽象類別型。 您可以使用繼承自<xref:System.Windows.Documents.TextElement>的其他類型。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>可包含 TextElement 物件的類型  
 請參閱[WPF 內容模型](../controls/wpf-content-model.md)。  
  
## <a name="see-also"></a>另請參閱

- [透過 Blocks 屬性管理 FlowDocument](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [透過 Blocks 屬性管理非固定格式內容元素](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [透過 Blocks 屬性管理 FlowDocument](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [透過 Columns 屬性管理表格的資料行](how-to-manipulate-table-columns-through-the-columns-property.md)
- [透過 RowGroups 屬性管理表格的資料列群組](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
