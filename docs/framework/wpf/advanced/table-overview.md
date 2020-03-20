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
# <a name="table-overview"></a><span data-ttu-id="73e3d-102">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="73e3d-102">Table Overview</span></span>
<span data-ttu-id="73e3d-103"><xref:System.Windows.Documents.Table>是支援基於網格的 Flow 文檔內容的塊級元素。</span><span class="sxs-lookup"><span data-stu-id="73e3d-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="73e3d-104">此元素的彈性讓它更為實用，但也讓您更難了解並正確使用。</span><span class="sxs-lookup"><span data-stu-id="73e3d-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="73e3d-105">本主題包含下列各節。</span><span class="sxs-lookup"><span data-stu-id="73e3d-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="73e3d-106">表格的基本概念</span><span class="sxs-lookup"><span data-stu-id="73e3d-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="73e3d-107">表格與方格之間的差異</span><span class="sxs-lookup"><span data-stu-id="73e3d-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="73e3d-108">基本的表格結構</span><span class="sxs-lookup"><span data-stu-id="73e3d-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="73e3d-109">表格內含項目</span><span class="sxs-lookup"><span data-stu-id="73e3d-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="73e3d-110">資料列群組</span><span class="sxs-lookup"><span data-stu-id="73e3d-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="73e3d-111">背景轉譯優先順序</span><span class="sxs-lookup"><span data-stu-id="73e3d-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="73e3d-112">跨越資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="73e3d-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="73e3d-113">使用程式碼建置表格</span><span class="sxs-lookup"><span data-stu-id="73e3d-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="73e3d-114">[相關主題]</span><span class="sxs-lookup"><span data-stu-id="73e3d-114">[Related Topics]</span></span>
  
<a name="table_basics"></a>
## <a name="table-basics"></a><span data-ttu-id="73e3d-115">表格的基本概念</span><span class="sxs-lookup"><span data-stu-id="73e3d-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="73e3d-116">表格與方格之間的差異</span><span class="sxs-lookup"><span data-stu-id="73e3d-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="73e3d-117"><xref:System.Windows.Documents.Table>並<xref:System.Windows.Controls.Grid>共用一些通用功能，但每個功能最適合不同的方案。</span><span class="sxs-lookup"><span data-stu-id="73e3d-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="73e3d-118">A<xref:System.Windows.Documents.Table>設計用於流內容中（有關流內容的詳細資訊，請參閱[流文檔概述](flow-document-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="73e3d-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="73e3d-119">方格最適合在表單內部使用 (基本上，是在非固定格式內容以外的任何地方)。</span><span class="sxs-lookup"><span data-stu-id="73e3d-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="73e3d-120">在<xref:System.Windows.Documents.FlowDocument>中<xref:System.Windows.Documents.Table>，支援流內容行為，如分頁、列重流和內容選擇，而<xref:System.Windows.Controls.Grid>不支援。</span><span class="sxs-lookup"><span data-stu-id="73e3d-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="73e3d-121">另<xref:System.Windows.Controls.Grid>一方面，由於許多原因，包括<xref:System.Windows.Documents.FlowDocument><xref:System.Windows.Controls.Grid>添加基於行和列索引的元素，<xref:System.Windows.Documents.Table>最好在 外部使用。</span><span class="sxs-lookup"><span data-stu-id="73e3d-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="73e3d-122">該<xref:System.Windows.Controls.Grid>元素允許分層子內容，允許多個元素存在於單個"儲存格"中。</span><span class="sxs-lookup"><span data-stu-id="73e3d-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="73e3d-123"><xref:System.Windows.Documents.Table>不支援分層。</span><span class="sxs-lookup"><span data-stu-id="73e3d-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="73e3d-124">子<xref:System.Windows.Controls.Grid>元素的子項目可以相對於其"儲存格"邊界區域絕對位置。</span><span class="sxs-lookup"><span data-stu-id="73e3d-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="73e3d-125"><xref:System.Windows.Documents.Table>不支援此功能。</span><span class="sxs-lookup"><span data-stu-id="73e3d-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="73e3d-126">最後，A<xref:System.Windows.Controls.Grid>需要更少的資源，<xref:System.Windows.Documents.Table>然後考慮使用<xref:System.Windows.Controls.Grid>a 來提高性能。</span><span class="sxs-lookup"><span data-stu-id="73e3d-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a><span data-ttu-id="73e3d-127">基本的表格結構</span><span class="sxs-lookup"><span data-stu-id="73e3d-127">Basic Table Structure</span></span>  
 <span data-ttu-id="73e3d-128"><xref:System.Windows.Documents.Table>提供基於網格的表示，由列（由<xref:System.Windows.Documents.TableColumn>元素表示）和行（由<xref:System.Windows.Documents.TableRow>元素表示）。</span><span class="sxs-lookup"><span data-stu-id="73e3d-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="73e3d-129"><xref:System.Windows.Documents.TableColumn>元素不承載內容;元素不承載內容。它們只定義列和列的特徵。</span><span class="sxs-lookup"><span data-stu-id="73e3d-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="73e3d-130"><xref:System.Windows.Documents.TableRow>元素必須託管在一個<xref:System.Windows.Documents.TableRowGroup>元素中，該元素定義表的行分組。</span><span class="sxs-lookup"><span data-stu-id="73e3d-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="73e3d-131"><xref:System.Windows.Documents.TableCell>元素包含表要顯示的實際內容，必須託管在<xref:System.Windows.Documents.TableRow>元素中。</span><span class="sxs-lookup"><span data-stu-id="73e3d-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="73e3d-132"><xref:System.Windows.Documents.TableCell>可能只包含派生自<xref:System.Windows.Documents.Block>的元素。</span><span class="sxs-lookup"><span data-stu-id="73e3d-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="73e3d-133"><xref:System.Windows.Documents.TableCell>包括的有效子項目。</span><span class="sxs-lookup"><span data-stu-id="73e3d-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <span data-ttu-id="73e3d-134"><xref:System.Windows.Documents.TableCell>元素不能直接承載文本內容。</span><span class="sxs-lookup"><span data-stu-id="73e3d-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="73e3d-135">有關流內容元素的包含規則的詳細資訊，請參閱<xref:System.Windows.Documents.TableCell>流[文檔概述](flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="73e3d-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73e3d-136"><xref:System.Windows.Documents.Table>與元素類似，<xref:System.Windows.Controls.Grid>但具有更多功能，因此需要更大的資源開銷。</span><span class="sxs-lookup"><span data-stu-id="73e3d-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="73e3d-137">下面的示例定義了一個簡單的 2 x 3 表與 XAML。</span><span class="sxs-lookup"><span data-stu-id="73e3d-137">The following example defines a simple 2 x 3 table with XAML.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="73e3d-138">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="73e3d-138">The following figure shows how this example renders.</span></span>  
  
 ![顯示基本表呈現方式的螢幕截圖。](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a><span data-ttu-id="73e3d-140">表格內含項目</span><span class="sxs-lookup"><span data-stu-id="73e3d-140">Table Containment</span></span>  
 <span data-ttu-id="73e3d-141"><xref:System.Windows.Documents.Table>派生自元素<xref:System.Windows.Documents.Block>，並遵循<xref:System.Windows.Documents.Block>級別元素的通用規則。</span><span class="sxs-lookup"><span data-stu-id="73e3d-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="73e3d-142">元素<xref:System.Windows.Documents.Table>可以由以下任何元素包含：</span><span class="sxs-lookup"><span data-stu-id="73e3d-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a><span data-ttu-id="73e3d-143">資料列群組</span><span class="sxs-lookup"><span data-stu-id="73e3d-143">Row Groupings</span></span>  
 <span data-ttu-id="73e3d-144">該<xref:System.Windows.Documents.TableRowGroup>元素提供了一種對表中的行進行任意分組的方法;表中的每一行都必須屬於行分組。</span><span class="sxs-lookup"><span data-stu-id="73e3d-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="73e3d-145">資料列群組內的資料列通常會共用相同的意圖，也可能會設計成一個群組。</span><span class="sxs-lookup"><span data-stu-id="73e3d-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="73e3d-146">資料列群組的常見用法是從表格所包含的主要內容中將特殊用途的資料列分隔開來，例如，標題、頁首和頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="73e3d-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="73e3d-147">下面的示例使用 XAML 定義具有樣式標題和頁腳行的表。</span><span class="sxs-lookup"><span data-stu-id="73e3d-147">The following example uses XAML to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="73e3d-148">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="73e3d-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="73e3d-149">![螢幕擷取畫面：資料表資料列群組](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="73e3d-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>
### <a name="background-rendering-precedence"></a><span data-ttu-id="73e3d-150">背景轉譯優先順序</span><span class="sxs-lookup"><span data-stu-id="73e3d-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="73e3d-151">表格元素會依下列順序 (從最低到最高的疊置順序) 來轉譯。</span><span class="sxs-lookup"><span data-stu-id="73e3d-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="73e3d-152">此順序無法改變。</span><span class="sxs-lookup"><span data-stu-id="73e3d-152">This order cannot be changed.</span></span> <span data-ttu-id="73e3d-153">例如，您可以用來覆寫這個已建立之順序的這些元素不具任何「疊置順序」屬性。</span><span class="sxs-lookup"><span data-stu-id="73e3d-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="73e3d-154">請考慮下列範例，其會針對表格內這其中每一個元素定義背景色彩。</span><span class="sxs-lookup"><span data-stu-id="73e3d-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="73e3d-155">下圖顯示此範例的轉譯方式 (僅顯示背景色彩)。</span><span class="sxs-lookup"><span data-stu-id="73e3d-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="73e3d-156">![螢幕截圖：表 z&#45;順序](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="73e3d-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="73e3d-157">跨越資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="73e3d-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="73e3d-158">表儲存格可以分別配置為使用<xref:System.Windows.Documents.TableCell.RowSpan%2A>或 屬性跨越多個行或<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>列。</span><span class="sxs-lookup"><span data-stu-id="73e3d-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="73e3d-159">請考慮下列範例，其中有一個儲存格會跨越三個資料行。</span><span class="sxs-lookup"><span data-stu-id="73e3d-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="73e3d-160">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="73e3d-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="73e3d-161">![螢幕擷取畫面：儲存格合併三欄](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="73e3d-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a><span data-ttu-id="73e3d-162">使用程式碼建置表格</span><span class="sxs-lookup"><span data-stu-id="73e3d-162">Building a Table With Code</span></span>  
 <span data-ttu-id="73e3d-163">以下示例演示如何以程式設計方式創建 和<xref:System.Windows.Documents.Table>填充內容。</span><span class="sxs-lookup"><span data-stu-id="73e3d-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="73e3d-164">表的內容被分攤成五行（由<xref:System.Windows.Documents.TableRow><xref:System.Windows.Documents.Table.RowGroups%2A>包含在物件中的物件表示）和六列（由<xref:System.Windows.Documents.TableColumn>物件表示）。</span><span class="sxs-lookup"><span data-stu-id="73e3d-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="73e3d-165">資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="73e3d-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="73e3d-166">請注意，「標題」、「標頭」和「頁尾」資料列的概念不是資料表固有的；這些只是具有不同特性的資料列。</span><span class="sxs-lookup"><span data-stu-id="73e3d-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="73e3d-167">表儲存格包含實際內容，內容可以由文本、圖像或幾乎任何其他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]元素組成。</span><span class="sxs-lookup"><span data-stu-id="73e3d-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="73e3d-168">首先，將<xref:System.Windows.Documents.FlowDocument>創建 承載 的<xref:System.Windows.Documents.Table>，並創建<xref:System.Windows.Documents.Table>一個新內容並將其添加到 中<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="73e3d-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="73e3d-169">接下來，將<xref:System.Windows.Documents.TableColumn>創建六個物件並將其添加到表的集合<xref:System.Windows.Documents.Table.Columns%2A>中，並應用了一些格式。</span><span class="sxs-lookup"><span data-stu-id="73e3d-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73e3d-170">請注意，表的集合<xref:System.Windows.Documents.Table.Columns%2A>使用標準的零基索引。</span><span class="sxs-lookup"><span data-stu-id="73e3d-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="73e3d-171">接下來，建立標題資料列，並新增至已套用某些格式的資料表。</span><span class="sxs-lookup"><span data-stu-id="73e3d-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="73e3d-172">標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。</span><span class="sxs-lookup"><span data-stu-id="73e3d-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="73e3d-173">接著，建立標頭資料列並新增至資料表，然後在標頭資料列中建立儲存格並填入內容。</span><span class="sxs-lookup"><span data-stu-id="73e3d-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="73e3d-174">接下來，建立資料的資料列並新增至資料表，然後在此資料列中建立儲存格並填入內容。</span><span class="sxs-lookup"><span data-stu-id="73e3d-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="73e3d-175">建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="73e3d-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="73e3d-176">最後，建立並新增頁尾資料列，然後設定格式。</span><span class="sxs-lookup"><span data-stu-id="73e3d-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="73e3d-177">如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。</span><span class="sxs-lookup"><span data-stu-id="73e3d-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="73e3d-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73e3d-178">See also</span></span>

- [<span data-ttu-id="73e3d-179">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="73e3d-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="73e3d-180">使用 XAML 定義資料表</span><span class="sxs-lookup"><span data-stu-id="73e3d-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="73e3d-181">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="73e3d-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="73e3d-182">使用動態內容項目</span><span class="sxs-lookup"><span data-stu-id="73e3d-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
