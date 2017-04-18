---
title: "資料表概觀 | Microsoft Docs"
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
  - "文件, 資料表"
  - "非固定格式內容項目 [WPF], 資料表"
  - "資料表"
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 資料表概觀
<xref:System.Windows.Documents.Table> 是一個支援以方格顯示非固定格式文件內容的區塊層級項目。  此項目的彈性增加了它的實用性，但也使其更難以了解及正確使用。  
  
 本主題包含下列章節。  
  
-   [資料表的基本概念](#table_basics)  
  
-   [資料表與方格有何不同](#table_vs_Grid)  
  
-   [基本資料表結構](#basic_table_structure)  
  
-   [資料表內含項目](#table_containment)  
  
-   [資料列群組](#row_groupings)  
  
-   [背景呈現優先順序](#rednering_precedence)  
  
-   [擴展資料列或資料行](#spanning_rows_or_columns)  
  
-   [使用程式碼建置資料表](#building_a_table_with_code)  
  
-   [相關主題](#see_also)  
  
<a name="table_basics"></a>   
## 資料表的基本概念  
  
<a name="table_vs_Grid"></a>   
### 資料表與方格有何不同  
 <xref:System.Windows.Documents.Table> 與 <xref:System.Windows.Controls.Grid> 會共用某些通用功能，但兩者分別適用於不同的情況。  <xref:System.Windows.Documents.Table> 的設計適合在非固定格式內容中使用 \(如需非固定格式內容的詳細資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)\)。  方格則適用於表單內 \(基本上，只要是非固定格式內容都適用\)。  在 <xref:System.Windows.Documents.FlowDocument> 內，<xref:System.Windows.Documents.Table> 支援分頁、資料行重新排列與內容選取等非固定格式內容行為，而 <xref:System.Windows.Controls.Grid> 則否。  另一方面，<xref:System.Windows.Controls.Grid> 適用於 <xref:System.Windows.Documents.FlowDocument> 以外的地方，其原因眾多，包括 <xref:System.Windows.Controls.Grid> 會根據資料列與資料行索引加入項目，<xref:System.Windows.Documents.Table> 則否。  <xref:System.Windows.Controls.Grid> 項目可允許將子內容分層，所以單一「儲存格」中可以有多個項目。<xref:System.Windows.Documents.Table> 不支援分層。  <xref:System.Windows.Controls.Grid> 的子項目可放在相對於其「儲存格」界限區域的絕對位置。  但 <xref:System.Windows.Documents.Table> 不支援此功能。  最後，<xref:System.Windows.Controls.Grid> 所需的資源比 <xref:System.Windows.Documents.Table> 少，因此請考慮使用 <xref:System.Windows.Controls.Grid> 提升效能。  
  
<a name="basic_table_structure"></a>   
### 基本資料表結構  
 <xref:System.Windows.Documents.Table> 可提供由資料行 \(以 <xref:System.Windows.Documents.TableColumn> 項目代表\) 與資料列 \(以 <xref:System.Windows.Documents.TableRow> 項目代表\) 組成的方格式顯示。  <xref:System.Windows.Documents.TableColumn> 項目不會裝載內容；只會定義資料行和資料行的特性。  <xref:System.Windows.Documents.TableRow> 項目必須裝載於 <xref:System.Windows.Documents.TableRowGroup> 項目中，而該項目會定義資料表的資料列群組。  <xref:System.Windows.Documents.TableCell> 項目包含要以資料表代表的實際內容，且必須裝載於 <xref:System.Windows.Documents.TableRow> 項目中。  <xref:System.Windows.Documents.TableCell> 只能包含衍生自 <xref:System.Windows.Documents.Block> 的項目。  也包括 <xref:System.Windows.Documents.TableCell> 的有效子項目。  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> 項目不可直接裝載文字內容。  若需 <xref:System.Windows.Documents.TableCell> 等非固定格式內容項目之內含項目規則的詳細資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> 類似於 <xref:System.Windows.Controls.Grid> 項目，但其功能較多，因此需要更多資源負荷。  
  
 下列範例使用 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 定義簡單的 2 x 3 資料表。  
  
 [!code-xml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 下圖顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：呈現基本資料表](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### 資料表內含項目  
 <xref:System.Windows.Documents.Table> 衍生自 <xref:System.Windows.Documents.Block> 項目，且必須遵循 <xref:System.Windows.Documents.Block> 層級項目的一般規則。  <xref:System.Windows.Documents.Table> 項目可包含在下列任何項目中：  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### 資料列群組  
 <xref:System.Windows.Documents.TableRowGroup> 項目提供一種方法，可以任意將資料表內的資料列放在一起形成群組；資料表中的每一資料列都必須屬於一個資料列群組。  資料列群組內的資料列通常會有相同的目的，而且可將樣式設計成同一個群組。  資料列群組的常見使用方式，是從資料表內含的主要內容區隔出特殊用途的資料列，如標題、頁首與頁尾 \(Footer\) 資料列。  
  
 下列範例使用 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 定義資料表，並設定其中頁首與頁尾資料列的樣式。  
  
 [!code-xml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 下圖顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：資料表資料列群組](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table\_RowGroups")  
  
<a name="renderning_precedence"></a>   
### 背景呈現優先順序  
 資料表項目會以下列順序呈現 \(由低至高的[疊置順序](GTMT)\)。  此順序不可變更。  例如，這些項目並沒有「疊置順序」屬性以用來覆寫已建立之順序。  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 請考量下列範例，此範例會定義資料表中前述每個項目的背景色彩。  
  
 [!code-xml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 下圖顯示此範例所呈現的內容 \(僅顯示背景色彩\)。  
  
 ![螢幕擷取畫面：資料表疊置順序](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table\_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### 擴展資料列或資料行  
 資料表儲存格可分別使用 <xref:System.Windows.Documents.TableCell.RowSpan%2A> 或 <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> 屬性進行設定，以擴展多個資料列或資料行。  
  
 請考量下列範例，其中的儲存格擴展至三個資料行。  
  
 [!code-xml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 下圖顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：儲存格合併三欄](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table\_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## 使用程式碼建置資料表  
 下列範例顯示如何以程式設計的方式建立 <xref:System.Windows.Documents.Table> 並為其填入內容。  資料表的內容會分配到五個資料列 \(以 <xref:System.Windows.Documents.Table.RowGroups%2A> 物件中所含的 <xref:System.Windows.Documents.TableRow> 物件表示\) 及六個資料行 \(以 <xref:System.Windows.Documents.TableColumn> 物件表示\) 中。  這些資料列分別用於不同的顯示用途，包括為整個資料表下標的標題資料列、用以說明資料表中各資料行的頁首資料列，以及具有摘要資訊的頁尾資料列。  請注意，「標題」、「頁首」與「頁尾」等資料列的概念並非資料表原本所固有，它們只是具有不同特性的資料列。  資料表儲存格含有實際的內容，其中可包含文字、影像或其他幾乎所有的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 項目。  
  
 首先，建立 <xref:System.Windows.Documents.FlowDocument> 以裝載 <xref:System.Windows.Documents.Table>，然後建立新的 <xref:System.Windows.Documents.Table> 並將其加入至 <xref:System.Windows.Documents.FlowDocument> 的內容中。  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 接著，建立六個 <xref:System.Windows.Documents.TableColumn> 物件，並將其加入至資料表的 <xref:System.Windows.Documents.Table.Columns%2A> 集合中，並為其套用某格式。  
  
> [!NOTE]
>  請注意，資料表的 <xref:System.Windows.Documents.Table.Columns%2A> 集合使用以零起始的標準索引。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 接下來建立標題資料列，並將其加入至資料表中並套用某格式。  標題資料列包含單一儲存格，但擴展至資料表中全部六個資料行。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 接著建立頁首資料列，並將其加入至資料表中，頁首資料列中會建立儲存格，並填入內容。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 接著建立資料的資料列，並將其加入至資料表中，此資料列中會建立儲存格，並填入內容。  建置此資料列與建置頁首資料列相似，差別在於套用的格式略有不同。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 最後建立頁尾資料列，並將其加入與格式化。  與標題資料列相同，頁尾也包含單一儲存格但擴展至資料表中全部六個資料行。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## 請參閱  
 [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [使用 XAML 定義資料表](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [使用非固定格式項目](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)