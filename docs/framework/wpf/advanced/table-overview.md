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
ms.openlocfilehash: 0888bc213be6b8037d0574bb5f9ac76e7651491a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745359"
---
# <a name="table-overview"></a>資料表概觀
<xref:System.Windows.Documents.Table> 是支援的非固定格式文件內容的方格呈現的區塊層級項目。 此元素的彈性讓它更為實用，但也讓您更難了解並正確使用。  
  
 此主題包括下列各節。  
  
-   [表格的基本概念](#table_basics)  
  
-   [表格與方格之間的差異](#table_vs_Grid)  
  
-   [基本的表格結構](#basic_table_structure)  
  
-   [表格內含項目](#table_containment)  
  
-   [資料列群組](#row_groupings)  
  
-   [背景轉譯優先順序](#rendering_precedence)  
  
-   [跨越資料列和資料行](#spanning_rows_or_columns)  
  
-   [使用程式碼建置表格](#building_a_table_with_code)  
  
-   [相關主題] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>表格的基本概念  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>表格與方格之間的差異  
 <xref:System.Windows.Documents.Table> 和<xref:System.Windows.Controls.Grid>共用一些通用的功能，但每一個都是最適合用於不同的案例。 A<xref:System.Windows.Documents.Table>適用於非固定格式內容中 (請參閱 <<c2> [ 非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)如需有關非固定格式內容)。 方格最適合在表單內部使用 (基本上，是在非固定格式內容以外的任何地方)。 內<xref:System.Windows.Documents.FlowDocument>，<xref:System.Windows.Documents.Table>支援非固定格式內容的行為，例如分頁、 資料行自動重排及內容選取範圍時<xref:System.Windows.Controls.Grid>則否。 A<xref:System.Windows.Controls.Grid>另一方面最適合用於外部<xref:System.Windows.Documents.FlowDocument>許多原因，包括<xref:System.Windows.Controls.Grid>將根據資料列和資料行的索引，項目加入<xref:System.Windows.Documents.Table>則否。 <xref:System.Windows.Controls.Grid>元素允許對子內容分層，可讓一個以上的項目存在於單一 「 儲存格。 」 <xref:System.Windows.Documents.Table> 不支援分層。 子項目的<xref:System.Windows.Controls.Grid>可以相對於其 「 儲存格 」 界限區域的絕對位置。 <xref:System.Windows.Documents.Table> 不支援這項功能。 最後，<xref:System.Windows.Controls.Grid>需要較少的資源則會顯示<xref:System.Windows.Documents.Table>因此，請考慮使用<xref:System.Windows.Controls.Grid>以改善效能。  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>基本的表格結構  
 <xref:System.Windows.Documents.Table> 提供以方格為基礎的簡報，其中包含資料行 (由<xref:System.Windows.Documents.TableColumn>項目) 和資料列 (由<xref:System.Windows.Documents.TableRow>項目)。 <xref:System.Windows.Documents.TableColumn> 項目不會裝載內容;此外，它們只會定義資料行和資料行的特性。 <xref:System.Windows.Documents.TableRow> 元素必須裝載於<xref:System.Windows.Documents.TableRowGroup>元素，其定義的資料表資料列群組。 <xref:System.Windows.Documents.TableCell> 項目，其中包含要呈現資料表的實際內容，必須裝載在<xref:System.Windows.Documents.TableRow>項目。 <xref:System.Windows.Documents.TableCell> 只能包含衍生自<xref:System.Windows.Documents.Block>。  有效的子項目<xref:System.Windows.Documents.TableCell>包含。  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> 項目可能不會直接裝載文字內容。 如需有關非固定格式的內含項目規則內容的項目喜歡<xref:System.Windows.Documents.TableCell>，請參閱 <<c2> [ 非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> 類似於<xref:System.Windows.Controls.Grid>元素但具有更多的功能，因此需要更高的資源負荷。  
  
 下列範例會定義簡單的 2 x 3 表格與[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]。  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![螢幕擷取畫面：轉譯基本表格](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>表格內含項目  
 <xref:System.Windows.Documents.Table> 衍生自<xref:System.Windows.Documents.Block>項目，並遵循的一般規則<xref:System.Windows.Documents.Block>層級項目。  A<xref:System.Windows.Documents.Table>元素可能包含任何下列的項目：  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>資料列群組  
 <xref:System.Windows.Documents.TableRowGroup>項目會提供用來在任意資料表內的群組資料列; 資料表中的每個資料列必須屬於一個資料列群組。  資料列群組內的資料列通常會共用相同的意圖，也可能會設計成一個群組。  資料列群組的常見用法是從表格所包含的主要內容中將特殊用途的資料列分隔開來，例如，標題、頁首和頁尾資料列。  
  
 下列範例會使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]定義具有已設定樣式的頁首及頁尾資料列的資料表。  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![螢幕擷取畫面：資料表資料列分組](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>背景轉譯優先順序  
 表格元素會依下列順序 (從最低到最高的疊置順序) 來轉譯。 此順序無法改變。 例如，您可以用來覆寫這個已建立之順序的這些元素不具任何「疊置順序」屬性。  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 請考慮下列範例，其會針對表格內這其中每一個元素定義背景色彩。  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 下圖顯示此範例的轉譯方式 (僅顯示背景色彩)。  
  
 ![螢幕擷取畫面：資料表 z&#45;順序](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>跨越資料列和資料行  
 表格儲存格可能設定成使用跨越多個資料列或資料行<xref:System.Windows.Documents.TableCell.RowSpan%2A>或<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>屬性分別。  
  
 請考慮下列範例，其中有一個儲存格會跨越三個資料行。  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![螢幕擷取畫面：資料格跨越所有三個資料行](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>使用程式碼建置表格  
 下列範例示範如何以程式設計方式建立<xref:System.Windows.Documents.Table>並填入內容。 資料表的內容會分配到五個資料列 (由<xref:System.Windows.Documents.TableRow>中所包含的物件<xref:System.Windows.Documents.Table.RowGroups%2A>物件) 和六個資料行 (由<xref:System.Windows.Documents.TableColumn>物件)。 資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。  請注意，「標題」、「標頭」和「頁尾」資料列的概念不是表格固有的；這些只是具有不同特性的資料列。 資料表資料格包含實際的內容，其中包括文字、 影像或幾乎任何其他的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]項目。  
  
 首先，<xref:System.Windows.Documents.FlowDocument>建立主機<xref:System.Windows.Documents.Table>，和新<xref:System.Windows.Documents.Table>已建立並加入內容<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 接下來的六<xref:System.Windows.Documents.TableColumn>會建立物件，並將其加入資料表的<xref:System.Windows.Documents.Table.Columns%2A>套用某些格式的集合。  
  
> [!NOTE]
>  請注意，資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合會使用標準的以零為起始索引。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 接下來，建立標題資料列並新增至已套用某些格式的表格。  標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 接著，建立標頭資料列並新增至表格，然後在標頭資料列中建立儲存格並填入內容。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 接下來，建立資料的資料列並新增至表格，然後在此資料列中建立儲存格並填入內容。  建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 最後，建立並新增頁尾資料列，然後設定格式。  如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>另請參閱
- [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
- [使用 XAML 定義表格](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)
- [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [使用非固定格式元素](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
