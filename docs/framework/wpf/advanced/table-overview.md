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
ms.openlocfilehash: 6485aa9f2094b734f796ff38a33f4e0d3434e004
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317658"
---
# <a name="table-overview"></a><span data-ttu-id="85646-102">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="85646-102">Table Overview</span></span>
<xref:System.Windows.Documents.Table> <span data-ttu-id="85646-103">是支援的非固定格式文件內容的方格呈現的區塊層級項目。</span><span class="sxs-lookup"><span data-stu-id="85646-103">is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="85646-104">此元素的彈性讓它更為實用，但也讓您更難了解並正確使用。</span><span class="sxs-lookup"><span data-stu-id="85646-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="85646-105">此主題包括下列各節。</span><span class="sxs-lookup"><span data-stu-id="85646-105">This topic contains the following sections.</span></span>  
  
-   [<span data-ttu-id="85646-106">表格的基本概念</span><span class="sxs-lookup"><span data-stu-id="85646-106">Table Basics</span></span>](#table_basics)  
  
-   [<span data-ttu-id="85646-107">表格與方格之間的差異</span><span class="sxs-lookup"><span data-stu-id="85646-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
-   [<span data-ttu-id="85646-108">基本的表格結構</span><span class="sxs-lookup"><span data-stu-id="85646-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
-   [<span data-ttu-id="85646-109">表格內含項目</span><span class="sxs-lookup"><span data-stu-id="85646-109">Table Containment</span></span>](#table_containment)  
  
-   [<span data-ttu-id="85646-110">資料列群組</span><span class="sxs-lookup"><span data-stu-id="85646-110">Row Groupings</span></span>](#row_groupings)  
  
-   [<span data-ttu-id="85646-111">背景轉譯優先順序</span><span class="sxs-lookup"><span data-stu-id="85646-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
-   [<span data-ttu-id="85646-112">跨越資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="85646-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
-   [<span data-ttu-id="85646-113">使用程式碼建置表格</span><span class="sxs-lookup"><span data-stu-id="85646-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
-   <span data-ttu-id="85646-114">[相關主題]</span><span class="sxs-lookup"><span data-stu-id="85646-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="85646-115">表格的基本概念</span><span class="sxs-lookup"><span data-stu-id="85646-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="85646-116">表格與方格之間的差異</span><span class="sxs-lookup"><span data-stu-id="85646-116">How is Table Different then Grid?</span></span>  
 <xref:System.Windows.Documents.Table> <span data-ttu-id="85646-117">和<xref:System.Windows.Controls.Grid>共用一些通用的功能，但每一個都是最適合用於不同的案例。</span><span class="sxs-lookup"><span data-stu-id="85646-117">and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="85646-118">A<xref:System.Windows.Documents.Table>適用於非固定格式內容中 (請參閱 <<c2> [ 非固定格式文件概觀](flow-document-overview.md)如需有關非固定格式內容)。</span><span class="sxs-lookup"><span data-stu-id="85646-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="85646-119">方格最適合在表單內部使用 (基本上，是在非固定格式內容以外的任何地方)。</span><span class="sxs-lookup"><span data-stu-id="85646-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="85646-120">內<xref:System.Windows.Documents.FlowDocument>，<xref:System.Windows.Documents.Table>支援非固定格式內容的行為，例如分頁、 資料行自動重排及內容選取範圍時<xref:System.Windows.Controls.Grid>則否。</span><span class="sxs-lookup"><span data-stu-id="85646-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="85646-121">A<xref:System.Windows.Controls.Grid>另一方面最適合用於外部<xref:System.Windows.Documents.FlowDocument>許多原因，包括<xref:System.Windows.Controls.Grid>將根據資料列和資料行的索引，項目加入<xref:System.Windows.Documents.Table>則否。</span><span class="sxs-lookup"><span data-stu-id="85646-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="85646-122"><xref:System.Windows.Controls.Grid>元素允許對子內容分層，可讓一個以上的項目存在於單一 「 儲存格。 」</span><span class="sxs-lookup"><span data-stu-id="85646-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <xref:System.Windows.Documents.Table> <span data-ttu-id="85646-123">不支援分層。</span><span class="sxs-lookup"><span data-stu-id="85646-123">does not support layering.</span></span> <span data-ttu-id="85646-124">子項目的<xref:System.Windows.Controls.Grid>可以相對於其 「 儲存格 」 界限區域的絕對位置。</span><span class="sxs-lookup"><span data-stu-id="85646-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <xref:System.Windows.Documents.Table> <span data-ttu-id="85646-125">不支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="85646-125">does not support this feature.</span></span> <span data-ttu-id="85646-126">最後，<xref:System.Windows.Controls.Grid>需要較少的資源則會顯示<xref:System.Windows.Documents.Table>因此，請考慮使用<xref:System.Windows.Controls.Grid>以改善效能。</span><span class="sxs-lookup"><span data-stu-id="85646-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="85646-127">基本的表格結構</span><span class="sxs-lookup"><span data-stu-id="85646-127">Basic Table Structure</span></span>  
 <xref:System.Windows.Documents.Table> <span data-ttu-id="85646-128">提供以方格為基礎的簡報，其中包含資料行 (由<xref:System.Windows.Documents.TableColumn>項目) 和資料列 (由<xref:System.Windows.Documents.TableRow>項目)。</span><span class="sxs-lookup"><span data-stu-id="85646-128">provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <xref:System.Windows.Documents.TableColumn> <span data-ttu-id="85646-129">項目不會裝載內容;此外，它們只會定義資料行和資料行的特性。</span><span class="sxs-lookup"><span data-stu-id="85646-129">elements do not host content; they simply define columns and characteristics of columns.</span></span> <xref:System.Windows.Documents.TableRow> <span data-ttu-id="85646-130">元素必須裝載於<xref:System.Windows.Documents.TableRowGroup>元素，其定義的資料表資料列群組。</span><span class="sxs-lookup"><span data-stu-id="85646-130">elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <xref:System.Windows.Documents.TableCell> <span data-ttu-id="85646-131">項目，其中包含要呈現資料表的實際內容，必須裝載在<xref:System.Windows.Documents.TableRow>項目。</span><span class="sxs-lookup"><span data-stu-id="85646-131">elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <xref:System.Windows.Documents.TableCell> <span data-ttu-id="85646-132">只能包含衍生自<xref:System.Windows.Documents.Block>。</span><span class="sxs-lookup"><span data-stu-id="85646-132">may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="85646-133">有效的子項目<xref:System.Windows.Documents.TableCell>包含。</span><span class="sxs-lookup"><span data-stu-id="85646-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> <span data-ttu-id="85646-134">項目可能不會直接裝載文字內容。</span><span class="sxs-lookup"><span data-stu-id="85646-134">elements may not directly host text content.</span></span> <span data-ttu-id="85646-135">如需有關非固定格式的內含項目規則內容的項目喜歡<xref:System.Windows.Documents.TableCell>，請參閱 <<c2> [ 非固定格式文件概觀](flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="85646-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> <span data-ttu-id="85646-136">類似於<xref:System.Windows.Controls.Grid>元素但具有更多的功能，因此需要更高的資源負荷。</span><span class="sxs-lookup"><span data-stu-id="85646-136">is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="85646-137">下列範例會定義簡單的 2 x 3 表格與[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="85646-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="85646-138">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="85646-138">The following figure shows how this example renders.</span></span>  
  
 ![如果螢幕擷取畫面顯示基本的資料表的轉譯方式。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="85646-140">表格內含項目</span><span class="sxs-lookup"><span data-stu-id="85646-140">Table Containment</span></span>  
 <xref:System.Windows.Documents.Table> <span data-ttu-id="85646-141">衍生自<xref:System.Windows.Documents.Block>項目，並遵循的一般規則<xref:System.Windows.Documents.Block>層級項目。</span><span class="sxs-lookup"><span data-stu-id="85646-141">derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="85646-142">A<xref:System.Windows.Documents.Table>元素可能包含任何下列的項目：</span><span class="sxs-lookup"><span data-stu-id="85646-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="85646-143">資料列群組</span><span class="sxs-lookup"><span data-stu-id="85646-143">Row Groupings</span></span>  
 <span data-ttu-id="85646-144"><xref:System.Windows.Documents.TableRowGroup>項目會提供用來在任意資料表內的群組資料列; 資料表中的每個資料列必須屬於一個資料列群組。</span><span class="sxs-lookup"><span data-stu-id="85646-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="85646-145">資料列群組內的資料列通常會共用相同的意圖，也可能會設計成一個群組。</span><span class="sxs-lookup"><span data-stu-id="85646-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="85646-146">資料列群組的常見用法是從表格所包含的主要內容中將特殊用途的資料列分隔開來，例如，標題、頁首和頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="85646-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="85646-147">下列範例會使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]定義具有已設定樣式的頁首及頁尾資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="85646-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="85646-148">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="85646-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="85646-149">![螢幕擷取畫面：資料表資料列分組](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="85646-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="85646-150">背景轉譯優先順序</span><span class="sxs-lookup"><span data-stu-id="85646-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="85646-151">表格元素會依下列順序 (從最低到最高的疊置順序) 來轉譯。</span><span class="sxs-lookup"><span data-stu-id="85646-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="85646-152">此順序無法改變。</span><span class="sxs-lookup"><span data-stu-id="85646-152">This order cannot be changed.</span></span> <span data-ttu-id="85646-153">例如，您可以用來覆寫這個已建立之順序的這些元素不具任何「疊置順序」屬性。</span><span class="sxs-lookup"><span data-stu-id="85646-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="85646-154">請考慮下列範例，其會針對表格內這其中每一個元素定義背景色彩。</span><span class="sxs-lookup"><span data-stu-id="85646-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="85646-155">下圖顯示此範例的轉譯方式 (僅顯示背景色彩)。</span><span class="sxs-lookup"><span data-stu-id="85646-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="85646-156">![螢幕擷取畫面：資料表 z&#45;順序](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="85646-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="85646-157">跨越資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="85646-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="85646-158">表格儲存格可能設定成使用跨越多個資料列或資料行<xref:System.Windows.Documents.TableCell.RowSpan%2A>或<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>屬性分別。</span><span class="sxs-lookup"><span data-stu-id="85646-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="85646-159">請考慮下列範例，其中有一個儲存格會跨越三個資料行。</span><span class="sxs-lookup"><span data-stu-id="85646-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="85646-160">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="85646-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="85646-161">![螢幕擷取畫面：資料格跨越所有三個資料行](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="85646-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="85646-162">使用程式碼建置表格</span><span class="sxs-lookup"><span data-stu-id="85646-162">Building a Table With Code</span></span>  
 <span data-ttu-id="85646-163">下列範例示範如何以程式設計方式建立<xref:System.Windows.Documents.Table>並填入內容。</span><span class="sxs-lookup"><span data-stu-id="85646-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="85646-164">資料表的內容會分配到五個資料列 (由<xref:System.Windows.Documents.TableRow>中所包含的物件<xref:System.Windows.Documents.Table.RowGroups%2A>物件) 和六個資料行 (由<xref:System.Windows.Documents.TableColumn>物件)。</span><span class="sxs-lookup"><span data-stu-id="85646-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="85646-165">資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="85646-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="85646-166">請注意，「標題」、「標頭」和「頁尾」資料列的概念不是表格固有的；這些只是具有不同特性的資料列。</span><span class="sxs-lookup"><span data-stu-id="85646-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="85646-167">資料表資料格包含實際的內容，其中包括文字、 影像或幾乎任何其他的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]項目。</span><span class="sxs-lookup"><span data-stu-id="85646-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="85646-168">首先，<xref:System.Windows.Documents.FlowDocument>建立主機<xref:System.Windows.Documents.Table>，和新<xref:System.Windows.Documents.Table>已建立並加入內容<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="85646-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="85646-169">接下來的六<xref:System.Windows.Documents.TableColumn>會建立物件，並將其加入資料表的<xref:System.Windows.Documents.Table.Columns%2A>套用某些格式的集合。</span><span class="sxs-lookup"><span data-stu-id="85646-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85646-170">請注意，資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合會使用標準的以零為起始索引。</span><span class="sxs-lookup"><span data-stu-id="85646-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="85646-171">接下來，建立標題資料列並新增至已套用某些格式的表格。</span><span class="sxs-lookup"><span data-stu-id="85646-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="85646-172">標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。</span><span class="sxs-lookup"><span data-stu-id="85646-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="85646-173">接著，建立標頭資料列並新增至表格，然後在標頭資料列中建立儲存格並填入內容。</span><span class="sxs-lookup"><span data-stu-id="85646-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="85646-174">接下來，建立資料的資料列並新增至表格，然後在此資料列中建立儲存格並填入內容。</span><span class="sxs-lookup"><span data-stu-id="85646-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="85646-175">建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="85646-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="85646-176">最後，建立並新增頁尾資料列，然後設定格式。</span><span class="sxs-lookup"><span data-stu-id="85646-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="85646-177">如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。</span><span class="sxs-lookup"><span data-stu-id="85646-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="85646-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85646-178">See also</span></span>

- [<span data-ttu-id="85646-179">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="85646-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="85646-180">使用 XAML 定義資料表</span><span class="sxs-lookup"><span data-stu-id="85646-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="85646-181">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="85646-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="85646-182">使用動態內容項目</span><span class="sxs-lookup"><span data-stu-id="85646-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
