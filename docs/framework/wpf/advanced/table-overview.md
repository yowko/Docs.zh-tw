---
title: "資料表概觀"
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
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb9edf0439c985af015d6badd11c026449a82f57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="table-overview"></a><span data-ttu-id="64210-102">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="64210-102">Table Overview</span></span>
<span data-ttu-id="64210-103"><xref:System.Windows.Documents.Table>是支援的非固定格式文件內容的方格呈現的區塊層級項目。</span><span class="sxs-lookup"><span data-stu-id="64210-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="64210-104">此元素的彈性讓它更為實用，但也讓您更難了解並正確使用。</span><span class="sxs-lookup"><span data-stu-id="64210-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="64210-105">此主題包括下列各節。</span><span class="sxs-lookup"><span data-stu-id="64210-105">This topic contains the following sections.</span></span>  
  
-   [<span data-ttu-id="64210-106">表格的基本概念</span><span class="sxs-lookup"><span data-stu-id="64210-106">Table Basics</span></span>](#table_basics)  
  
-   [<span data-ttu-id="64210-107">表格與方格之間的差異</span><span class="sxs-lookup"><span data-stu-id="64210-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
-   [<span data-ttu-id="64210-108">基本的表格結構</span><span class="sxs-lookup"><span data-stu-id="64210-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
-   [<span data-ttu-id="64210-109">表格內含項目</span><span class="sxs-lookup"><span data-stu-id="64210-109">Table Containment</span></span>](#table_containment)  
  
-   [<span data-ttu-id="64210-110">資料列群組</span><span class="sxs-lookup"><span data-stu-id="64210-110">Row Groupings</span></span>](#row_groupings)  
  
-   [<span data-ttu-id="64210-111">背景轉譯優先順序</span><span class="sxs-lookup"><span data-stu-id="64210-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
-   [<span data-ttu-id="64210-112">跨越資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="64210-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
-   [<span data-ttu-id="64210-113">使用程式碼建置表格</span><span class="sxs-lookup"><span data-stu-id="64210-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
-   <span data-ttu-id="64210-114">[相關主題]</span><span class="sxs-lookup"><span data-stu-id="64210-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="64210-115">表格的基本概念</span><span class="sxs-lookup"><span data-stu-id="64210-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="64210-116">表格與方格之間的差異</span><span class="sxs-lookup"><span data-stu-id="64210-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="64210-117"><xref:System.Windows.Documents.Table>和<xref:System.Windows.Controls.Grid>共用某些常見的功能，但每個最適合用於不同的案例。</span><span class="sxs-lookup"><span data-stu-id="64210-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="64210-118">A<xref:System.Windows.Documents.Table>適用於非固定格式內容中 (請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)如需有關非固定格式內容)。</span><span class="sxs-lookup"><span data-stu-id="64210-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="64210-119">方格最適合在表單內部使用 (基本上，是在非固定格式內容以外的任何地方)。</span><span class="sxs-lookup"><span data-stu-id="64210-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="64210-120">內<xref:System.Windows.Documents.FlowDocument>，<xref:System.Windows.Documents.Table>支援非固定格式內容的行為，例如分頁、 資料行重新排列，以及內容的選取範圍時<xref:System.Windows.Controls.Grid>則否。</span><span class="sxs-lookup"><span data-stu-id="64210-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="64210-121">A<xref:System.Windows.Controls.Grid>另一方面最適合用外部<xref:System.Windows.Documents.FlowDocument>有許多原因包括<xref:System.Windows.Controls.Grid>將根據資料列和資料行的索引，項目加入<xref:System.Windows.Documents.Table>則否。</span><span class="sxs-lookup"><span data-stu-id="64210-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="64210-122"><xref:System.Windows.Controls.Grid>項目可以讓圖層的子內容，讓一個以上的項目存在於單一 「 資料格 」。</span><span class="sxs-lookup"><span data-stu-id="64210-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="64210-123"><xref:System.Windows.Documents.Table>不支援的圖層。</span><span class="sxs-lookup"><span data-stu-id="64210-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="64210-124">子項目的<xref:System.Windows.Controls.Grid>可以相對於其 「 資料格 」 界限的區域絕對定位。</span><span class="sxs-lookup"><span data-stu-id="64210-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="64210-125"><xref:System.Windows.Documents.Table>不支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="64210-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="64210-126">最後，<xref:System.Windows.Controls.Grid>需要較少的資源則<xref:System.Windows.Documents.Table>因此請考慮使用<xref:System.Windows.Controls.Grid>來改善效能。</span><span class="sxs-lookup"><span data-stu-id="64210-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="64210-127">基本的表格結構</span><span class="sxs-lookup"><span data-stu-id="64210-127">Basic Table Structure</span></span>  
 <span data-ttu-id="64210-128"><xref:System.Windows.Documents.Table>提供格線為基礎的簡報，資料行所組成 (由<xref:System.Windows.Documents.TableColumn>項目) 和資料列 (由<xref:System.Windows.Documents.TableRow>項目)。</span><span class="sxs-lookup"><span data-stu-id="64210-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="64210-129"><xref:System.Windows.Documents.TableColumn>項目未裝載的內容。此外，它們只會定義資料行和資料行的特性。</span><span class="sxs-lookup"><span data-stu-id="64210-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="64210-130"><xref:System.Windows.Documents.TableRow>項目必須裝載在<xref:System.Windows.Documents.TableRowGroup>元素，其定義的資料表資料列群組。</span><span class="sxs-lookup"><span data-stu-id="64210-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="64210-131"><xref:System.Windows.Documents.TableCell>項目，其中包含資料表所呈現的實際內容，必須裝載在<xref:System.Windows.Documents.TableRow>項目。</span><span class="sxs-lookup"><span data-stu-id="64210-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="64210-132"><xref:System.Windows.Documents.TableCell>只能包含元素衍生自<xref:System.Windows.Documents.Block>。</span><span class="sxs-lookup"><span data-stu-id="64210-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="64210-133">有效的子項目<xref:System.Windows.Documents.TableCell>包含。</span><span class="sxs-lookup"><span data-stu-id="64210-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <span data-ttu-id="64210-134"><xref:System.Windows.Documents.TableCell>項目可能不會直接裝載文字內容。</span><span class="sxs-lookup"><span data-stu-id="64210-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="64210-135">如需有關資料流程的內含項目規則內容項目要<xref:System.Windows.Documents.TableCell>，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="64210-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64210-136"><xref:System.Windows.Documents.Table>類似於<xref:System.Windows.Controls.Grid>項目但了更多的功能，因此，您需要更高的資源負擔。</span><span class="sxs-lookup"><span data-stu-id="64210-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="64210-137">下列範例會定義簡單的 2 x 3 資料表與[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="64210-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="64210-138">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="64210-138">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="64210-139">![螢幕擷取畫面：轉譯基本表格](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")</span><span class="sxs-lookup"><span data-stu-id="64210-139">![Screenshot: Render a basic table](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")</span></span>  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="64210-140">表格內含項目</span><span class="sxs-lookup"><span data-stu-id="64210-140">Table Containment</span></span>  
 <span data-ttu-id="64210-141"><xref:System.Windows.Documents.Table>衍生自<xref:System.Windows.Documents.Block>項目，並遵循的一般規則<xref:System.Windows.Documents.Block>層級項目。</span><span class="sxs-lookup"><span data-stu-id="64210-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="64210-142">A<xref:System.Windows.Documents.Table>項目可能包含任何下列項目：</span><span class="sxs-lookup"><span data-stu-id="64210-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="64210-143">資料列群組</span><span class="sxs-lookup"><span data-stu-id="64210-143">Row Groupings</span></span>  
 <span data-ttu-id="64210-144"><xref:System.Windows.Documents.TableRowGroup>項目會提供用來在任意資料表內的群組資料列; 資料表中的每個資料列必須屬於資料列群組。</span><span class="sxs-lookup"><span data-stu-id="64210-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="64210-145">資料列群組內的資料列通常會共用相同的意圖，也可能會設計成一個群組。</span><span class="sxs-lookup"><span data-stu-id="64210-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="64210-146">資料列群組的常見用法是從表格所包含的主要內容中將特殊用途的資料列分隔開來，例如，標題、頁首和頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="64210-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="64210-147">下列範例會使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]定義具有已設定樣式的頁首及頁尾資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="64210-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="64210-148">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="64210-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="64210-149">![螢幕擷取畫面：表格資料列群組](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="64210-149">![Screenshot: Table row groups](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="64210-150">背景轉譯優先順序</span><span class="sxs-lookup"><span data-stu-id="64210-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="64210-151">表格元素會依下列順序 (從最低到最高的疊置順序) 來轉譯。</span><span class="sxs-lookup"><span data-stu-id="64210-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="64210-152">此順序無法改變。</span><span class="sxs-lookup"><span data-stu-id="64210-152">This order cannot be changed.</span></span> <span data-ttu-id="64210-153">例如，您可以用來覆寫這個已建立之順序的這些元素不具任何「疊置順序」屬性。</span><span class="sxs-lookup"><span data-stu-id="64210-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="64210-154">請考慮下列範例，其會針對表格內這其中每一個元素定義背景色彩。</span><span class="sxs-lookup"><span data-stu-id="64210-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="64210-155">下圖顯示此範例的轉譯方式 (僅顯示背景色彩)。</span><span class="sxs-lookup"><span data-stu-id="64210-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="64210-156">![螢幕擷取畫面︰表格疊置順序](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="64210-156">![Screenshot: Table z&#45;order](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="64210-157">跨越資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="64210-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="64210-158">表格儲存格可能設定成跨越多個資料列或資料行使用<xref:System.Windows.Documents.TableCell.RowSpan%2A>或<xref:System.Windows.Documents.TableCell.ColumnSpan%2A>分別屬性。</span><span class="sxs-lookup"><span data-stu-id="64210-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="64210-159">請考慮下列範例，其中有一個儲存格會跨越三個資料行。</span><span class="sxs-lookup"><span data-stu-id="64210-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="64210-160">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="64210-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="64210-161">![螢幕擷取畫面：儲存格跨越三個資料行](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="64210-161">![Screenshot: Cell spanning all three columns](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="64210-162">使用程式碼建置表格</span><span class="sxs-lookup"><span data-stu-id="64210-162">Building a Table With Code</span></span>  
 <span data-ttu-id="64210-163">下列範例顯示如何以程式設計方式建立<xref:System.Windows.Documents.Table>並填入內容。</span><span class="sxs-lookup"><span data-stu-id="64210-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="64210-164">資料表的內容分配到五個資料列 (由<xref:System.Windows.Documents.TableRow>所包含的物件<xref:System.Windows.Documents.Table.RowGroups%2A>物件) 和六個資料行 (由<xref:System.Windows.Documents.TableColumn>物件)。</span><span class="sxs-lookup"><span data-stu-id="64210-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="64210-165">資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="64210-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="64210-166">請注意，「標題」、「標頭」和「頁尾」資料列的概念不是表格固有的；這些只是具有不同特性的資料列。</span><span class="sxs-lookup"><span data-stu-id="64210-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="64210-167">資料表資料格包含實際的內容，其中可包含的文字、 影像或幾乎任何其他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]項目。</span><span class="sxs-lookup"><span data-stu-id="64210-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="64210-168">首先，<xref:System.Windows.Documents.FlowDocument>建立主機<xref:System.Windows.Documents.Table>，和新<xref:System.Windows.Documents.Table>已建立並加入至內容<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="64210-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="64210-169">接下來的六個<xref:System.Windows.Documents.TableColumn>物件會建立並加入至資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合中具有某些所套用的格式。</span><span class="sxs-lookup"><span data-stu-id="64210-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64210-170">請注意，資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合會使用標準的以零為起始索引。</span><span class="sxs-lookup"><span data-stu-id="64210-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="64210-171">接下來，建立標題資料列並新增至已套用某些格式的表格。</span><span class="sxs-lookup"><span data-stu-id="64210-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="64210-172">標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。</span><span class="sxs-lookup"><span data-stu-id="64210-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="64210-173">接著，建立標頭資料列並新增至表格，然後在標頭資料列中建立儲存格並填入內容。</span><span class="sxs-lookup"><span data-stu-id="64210-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="64210-174">接下來，建立資料的資料列並新增至表格，然後在此資料列中建立儲存格並填入內容。</span><span class="sxs-lookup"><span data-stu-id="64210-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="64210-175">建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="64210-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="64210-176">最後，建立並新增頁尾資料列，然後設定格式。</span><span class="sxs-lookup"><span data-stu-id="64210-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="64210-177">如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。</span><span class="sxs-lookup"><span data-stu-id="64210-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="64210-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64210-178">See Also</span></span>  
 [<span data-ttu-id="64210-179">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="64210-179">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="64210-180">使用 XAML 定義表格</span><span class="sxs-lookup"><span data-stu-id="64210-180">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="64210-181">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="64210-181">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="64210-182">使用非固定格式元素</span><span class="sxs-lookup"><span data-stu-id="64210-182">Use Flow Content Elements</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
