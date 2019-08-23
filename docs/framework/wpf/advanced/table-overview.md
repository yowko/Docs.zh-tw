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
ms.openlocfilehash: 01a5233a5436688caee3783cb26d344284df52e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964304"
---
# <a name="table-overview"></a>資料表概觀
<xref:System.Windows.Documents.Table>是區塊層級元素, 支援非固定格式檔內容的方格呈現方式。 此元素的彈性讓它更為實用，但也讓您更難了解並正確使用。  
  
 此主題包括下列各節。  
  
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
 <xref:System.Windows.Documents.Table>和<xref:System.Windows.Controls.Grid>共用一些常見的功能, 但每個都適用于不同的案例。 的<xref:System.Windows.Documents.Table>設計目的是要在非固定格式內容中使用 (如需有關「流動內容」的詳細資訊, 請參閱[flow 檔總覽](flow-document-overview.md))。 方格最適合在表單內部使用 (基本上，是在非固定格式內容以外的任何地方)。 在中<xref:System.Windows.Documents.Table> <xref:System.Windows.Controls.Grid> , 支援分頁、資料行重新排列和內容選取等非固定格式內容行為。 <xref:System.Windows.Documents.FlowDocument> 另一方面, 最好是<xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.Grid> <xref:System.Windows.Documents.Table>在之外使用, 因為有許多原因, 包括根據資料列和資料行索引來加入元素。 <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid>元素允許子內容的分層, 讓一個以上的專案存在於單一「資料格」內。 <xref:System.Windows.Documents.Table>不支援分層。 的子項目<xref:System.Windows.Controls.Grid>可以相對於其「儲存格」界限的區域進行絕對位置。 <xref:System.Windows.Documents.Table>不支援這項功能。 最後, <xref:System.Windows.Controls.Grid>需要較少的<xref:System.Windows.Documents.Table>資源, 因此請考慮使用<xref:System.Windows.Controls.Grid>來改善效能。  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>基本的表格結構  
 <xref:System.Windows.Documents.Table>提供由資料行 (以<xref:System.Windows.Documents.TableColumn>元素表示) 和資料列 (以專案<xref:System.Windows.Documents.TableRow>表示) 組成的方格型呈現。 <xref:System.Windows.Documents.TableColumn>元素不會裝載內容;它們只會定義資料行的資料行和特性。 <xref:System.Windows.Documents.TableRow>元素必須裝載于專案中<xref:System.Windows.Documents.TableRowGroup> , 以定義資料表的資料列群組。 <xref:System.Windows.Documents.TableCell>元素, 其中包含要由資料表呈現的實際內容, 必須裝載于<xref:System.Windows.Documents.TableRow>元素中。 <xref:System.Windows.Documents.TableCell>只能包含衍生自<xref:System.Windows.Documents.Block>的元素。  <xref:System.Windows.Documents.TableCell>包含的有效子項目。  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>元素可能不會直接裝載文字內容。 如需非固定格式<xref:System.Windows.Documents.TableCell>內容元素之內含專案規則的詳細資訊, 請參閱非固定格式[檔總覽](flow-document-overview.md)。  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>類似<xref:System.Windows.Controls.Grid>于元素, 但具有更多功能, 因此需要更大的資源額外負荷。  
  
 下列範例會使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]來定義一個簡單的 2 x 3 資料表。  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![顯示基本資料表呈現方式的螢幕擷取畫面。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>表格內含項目  
 <xref:System.Windows.Documents.Table>衍生自<xref:System.Windows.Documents.Block>元素, 並遵循<xref:System.Windows.Documents.Block>層級元素的通用規則。  <xref:System.Windows.Documents.Table>元素可能包含下列任何元素:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>資料列群組  
 <xref:System.Windows.Documents.TableRowGroup>元素可讓您任意分組資料表中的資料列; 資料表中的每個資料列都必須屬於資料列群組。  資料列群組內的資料列通常會共用相同的意圖，也可能會設計成一個群組。  資料列群組的常見用法是從表格所包含的主要內容中將特殊用途的資料列分隔開來，例如，標題、頁首和頁尾資料列。  
  
 下列範例會使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]來定義具有樣式頁首和頁尾資料列的資料表。  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![截取資料表資料列]群組(./media/table-rowgroups.png "Table_RowGroups")  
  
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
  
 ![截取表格 z&#45;順序](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>跨越資料列和資料行  
 您可以分別使用<xref:System.Windows.Documents.TableCell.RowSpan%2A>或<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>屬性, 將資料表資料格設定為跨越多個資料列或資料行。  
  
 請考慮下列範例，其中有一個儲存格會跨越三個資料行。  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![截取橫跨所有三個數據]行(./media/table-columnspan.png "Table_ColumnSpan")的資料格  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>使用程式碼建置表格  
 下列範例示範如何以程式設計方式建立<xref:System.Windows.Documents.Table> , 並在其中填入內容。 資料表的內容會分配為五個數據列 (以<xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.Table.RowGroups%2A>物件所包含的物件表示) 和<xref:System.Windows.Documents.TableColumn>六個數據行 (以物件表示)。 資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。  請注意，「標題」、「標頭」和「頁尾」資料列的概念不是表格固有的；這些只是具有不同特性的資料列。 資料表單元格包含實際內容, 其可由文字、影像或幾乎任何其他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]元素組成。  
  
 首先, <xref:System.Windows.Documents.FlowDocument>會建立來<xref:System.Windows.Documents.Table>裝載, 並<xref:System.Windows.Documents.FlowDocument>建立新<xref:System.Windows.Documents.Table>的, 並將其新增至的內容。  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 接下來, <xref:System.Windows.Documents.TableColumn>會建立六個物件, 並將其<xref:System.Windows.Documents.Table.Columns%2A>新增至資料表的集合, 並套用一些格式。  
  
> [!NOTE]
> 請注意, 資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合會使用標準的以零為起始的索引。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 接下來，建立標題資料列並新增至已套用某些格式的表格。  標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 接著，建立標頭資料列並新增至表格，然後在標頭資料列中建立儲存格並填入內容。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 接下來，建立資料的資料列並新增至表格，然後在此資料列中建立儲存格並填入內容。  建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 最後，建立並新增頁尾資料列，然後設定格式。  如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>另請參閱

- [非固定格式文件概觀](flow-document-overview.md)
- [使用 XAML 定義表格](how-to-define-a-table-with-xaml.md)
- [WPF 中的文件](documents-in-wpf.md)
- [使用非固定格式元素](how-to-use-flow-content-elements.md)
