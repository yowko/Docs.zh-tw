---
title: 資料表概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 4bd747cea43755116c56b16f1de9a6ffb59935ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187265"
---
# <a name="table-overview"></a>資料表概觀
<xref:System.Windows.Documents.Table>是支援基於網格的 Flow 文檔內容的塊級元素。 此元素的彈性讓它更為實用，但也讓您更難了解並正確使用。  
  
 本主題包含下列各節。  
  
- [表格的基本概念](#table_basics)  
  
- [表格與方格之間的差異](#table_vs_Grid)  
  
- [基本的表格結構](#basic_table_structure)  
  
- [表格內含項目](#table_containment)  
  
- [資料列群組](#row_groupings)  
  
- [背景轉譯優先順序](#rendering_precedence)  
  
- [跨越資料列和資料行](#spanning_rows_or_columns)  
  
- [使用程式碼建置表格](#building_a_table_with_code)  
  
- [相關主題]
  
<a name="table_basics"></a>
## <a name="table-basics"></a>表格的基本概念  
  
<a name="table_vs_Grid"></a>
### <a name="how-is-table-different-then-grid"></a>表格與方格之間的差異  
 <xref:System.Windows.Documents.Table>並<xref:System.Windows.Controls.Grid>共用一些通用功能，但每個功能最適合不同的方案。 A<xref:System.Windows.Documents.Table>設計用於流內容中（有關流內容的詳細資訊，請參閱[流文檔概述](flow-document-overview.md)）。 方格最適合在表單內部使用 (基本上，是在非固定格式內容以外的任何地方)。 在<xref:System.Windows.Documents.FlowDocument>中<xref:System.Windows.Documents.Table>，支援流內容行為，如分頁、列重流和內容選擇，而<xref:System.Windows.Controls.Grid>不支援。 另<xref:System.Windows.Controls.Grid>一方面，由於許多原因，包括<xref:System.Windows.Documents.FlowDocument><xref:System.Windows.Controls.Grid>添加基於行和列索引的元素，<xref:System.Windows.Documents.Table>最好在 外部使用。 該<xref:System.Windows.Controls.Grid>元素允許分層子內容，允許多個元素存在於單個"儲存格"中。 <xref:System.Windows.Documents.Table>不支援分層。 子<xref:System.Windows.Controls.Grid>元素的子項目可以相對於其"儲存格"邊界區域絕對位置。 <xref:System.Windows.Documents.Table>不支援此功能。 最後，A<xref:System.Windows.Controls.Grid>需要更少的資源，<xref:System.Windows.Documents.Table>然後考慮使用<xref:System.Windows.Controls.Grid>a 來提高性能。  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a>基本的表格結構  
 <xref:System.Windows.Documents.Table>提供基於網格的表示，由列（由<xref:System.Windows.Documents.TableColumn>元素表示）和行（由<xref:System.Windows.Documents.TableRow>元素表示）。 <xref:System.Windows.Documents.TableColumn>元素不承載內容;元素不承載內容。它們只定義列和列的特徵。 <xref:System.Windows.Documents.TableRow>元素必須託管在一個<xref:System.Windows.Documents.TableRowGroup>元素中，該元素定義表的行分組。 <xref:System.Windows.Documents.TableCell>元素包含表要顯示的實際內容，必須託管在<xref:System.Windows.Documents.TableRow>元素中。 <xref:System.Windows.Documents.TableCell>可能只包含派生自<xref:System.Windows.Documents.Block>的元素。  <xref:System.Windows.Documents.TableCell>包括的有效子項目。  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>元素不能直接承載文本內容。 有關流內容元素的包含規則的詳細資訊，請參閱<xref:System.Windows.Documents.TableCell>流[文檔概述](flow-document-overview.md)。  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>與元素類似，<xref:System.Windows.Controls.Grid>但具有更多功能，因此需要更大的資源開銷。  
  
 下面的示例定義了一個簡單的 2 x 3 表與 XAML。  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![顯示基本表呈現方式的螢幕截圖。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a>表格內含項目  
 <xref:System.Windows.Documents.Table>派生自元素<xref:System.Windows.Documents.Block>，並遵循<xref:System.Windows.Documents.Block>級別元素的通用規則。  元素<xref:System.Windows.Documents.Table>可以由以下任何元素包含：  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a>資料列群組  
 該<xref:System.Windows.Documents.TableRowGroup>元素提供了一種對表中的行進行任意分組的方法;表中的每一行都必須屬於行分組。  資料列群組內的資料列通常會共用相同的意圖，也可能會設計成一個群組。  資料列群組的常見用法是從表格所包含的主要內容中將特殊用途的資料列分隔開來，例如，標題、頁首和頁尾資料列。  
  
 下面的示例使用 XAML 定義具有樣式標題和頁腳行的表。  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![螢幕擷取畫面：資料表資料列群組](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>
### <a name="background-rendering-precedence"></a>背景轉譯優先順序  
 表格元素會依下列順序 (從最低到最高的疊置順序) 來轉譯。 此順序無法改變。 例如，您可以用來覆寫這個已建立之順序的這些元素不具任何「疊置順序」屬性。  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 請考慮下列範例，其會針對表格內這其中每一個元素定義背景色彩。  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 下圖顯示此範例的轉譯方式 (僅顯示背景色彩)。  
  
 ![螢幕截圖：表 z&#45;順序](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a>跨越資料列和資料行  
 表儲存格可以分別配置為使用<xref:System.Windows.Documents.TableCell.RowSpan%2A>或 屬性跨越多個行或<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>列。  
  
 請考慮下列範例，其中有一個儲存格會跨越三個資料行。  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![螢幕擷取畫面：儲存格合併三欄](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a>使用程式碼建置表格  
 以下示例演示如何以程式設計方式創建 和<xref:System.Windows.Documents.Table>填充內容。 表的內容被分攤成五行（由<xref:System.Windows.Documents.TableRow><xref:System.Windows.Documents.Table.RowGroups%2A>包含在物件中的物件表示）和六列（由<xref:System.Windows.Documents.TableColumn>物件表示）。 資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。  請注意，「標題」、「標頭」和「頁尾」資料列的概念不是資料表固有的；這些只是具有不同特性的資料列。 表儲存格包含實際內容，內容可以由文本、圖像或幾乎任何其他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]元素組成。  
  
 首先，將<xref:System.Windows.Documents.FlowDocument>創建 承載 的<xref:System.Windows.Documents.Table>，並創建<xref:System.Windows.Documents.Table>一個新內容並將其添加到 中<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 接下來，將<xref:System.Windows.Documents.TableColumn>創建六個物件並將其添加到表的集合<xref:System.Windows.Documents.Table.Columns%2A>中，並應用了一些格式。  
  
> [!NOTE]
> 請注意，表的集合<xref:System.Windows.Documents.Table.Columns%2A>使用標準的零基索引。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 接下來，建立標題資料列，並新增至已套用某些格式的資料表。  標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 接著，建立標頭資料列並新增至資料表，然後在標頭資料列中建立儲存格並填入內容。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 接下來，建立資料的資料列並新增至資料表，然後在此資料列中建立儲存格並填入內容。  建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 最後，建立並新增頁尾資料列，然後設定格式。  如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>另請參閱

- [非固定格式文件概觀](flow-document-overview.md)
- [使用 XAML 定義資料表](how-to-define-a-table-with-xaml.md)
- [WPF 中的文件](documents-in-wpf.md)
- [使用動態內容項目](how-to-use-flow-content-elements.md)
