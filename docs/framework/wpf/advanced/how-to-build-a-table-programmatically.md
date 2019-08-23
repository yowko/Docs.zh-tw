---
title: 作法：以程式設計方式建置資料表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 9c9061d3c4d6b3de5e1ab42a6b98c20813835ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964164"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="d48f7-102">作法：以程式設計方式建置資料表</span><span class="sxs-lookup"><span data-stu-id="d48f7-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="d48f7-103">下列範例示範如何以程式設計方式建立<xref:System.Windows.Documents.Table> , 並在其中填入內容。</span><span class="sxs-lookup"><span data-stu-id="d48f7-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="d48f7-104">資料表的內容會分配為五個數據列 (以<xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.Table.RowGroups%2A>物件所包含的物件表示) 和<xref:System.Windows.Documents.TableColumn>六個數據行 (以物件表示)。</span><span class="sxs-lookup"><span data-stu-id="d48f7-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="d48f7-105">資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="d48f7-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="d48f7-106">請注意，「標題」、「標頭」和「頁尾」資料列的概念不是表格固有的；這些只是具有不同特性的資料列。</span><span class="sxs-lookup"><span data-stu-id="d48f7-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="d48f7-107">資料表單元格包含實際內容, 其可由文字、影像或幾乎任何其他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]元素組成。</span><span class="sxs-lookup"><span data-stu-id="d48f7-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d48f7-108">範例</span><span class="sxs-lookup"><span data-stu-id="d48f7-108">Example</span></span>  
 <span data-ttu-id="d48f7-109">首先, <xref:System.Windows.Documents.FlowDocument>會建立來<xref:System.Windows.Documents.Table>裝載, 並<xref:System.Windows.Documents.FlowDocument>建立新<xref:System.Windows.Documents.Table>的, 並將其新增至的內容。</span><span class="sxs-lookup"><span data-stu-id="d48f7-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="d48f7-110">範例</span><span class="sxs-lookup"><span data-stu-id="d48f7-110">Example</span></span>  
 <span data-ttu-id="d48f7-111">接下來, <xref:System.Windows.Documents.TableColumn>會建立六個物件, 並將其<xref:System.Windows.Documents.Table.Columns%2A>新增至資料表的集合, 並套用一些格式。</span><span class="sxs-lookup"><span data-stu-id="d48f7-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d48f7-112">請注意, 資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合會使用標準的以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="d48f7-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="d48f7-113">範例</span><span class="sxs-lookup"><span data-stu-id="d48f7-113">Example</span></span>  
 <span data-ttu-id="d48f7-114">接下來，建立標題資料列，並新增至已套用某些格式的資料表。</span><span class="sxs-lookup"><span data-stu-id="d48f7-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="d48f7-115">標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。</span><span class="sxs-lookup"><span data-stu-id="d48f7-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="d48f7-116">範例</span><span class="sxs-lookup"><span data-stu-id="d48f7-116">Example</span></span>  
 <span data-ttu-id="d48f7-117">接著，建立標頭資料列並新增至表格，然後在標頭資料列中建立儲存格並填入內容。</span><span class="sxs-lookup"><span data-stu-id="d48f7-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="d48f7-118">範例</span><span class="sxs-lookup"><span data-stu-id="d48f7-118">Example</span></span>  
 <span data-ttu-id="d48f7-119">接下來，建立資料的資料列並新增至資料表，然後在此資料列中建立儲存格並填入內容。</span><span class="sxs-lookup"><span data-stu-id="d48f7-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="d48f7-120">建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="d48f7-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="d48f7-121">範例</span><span class="sxs-lookup"><span data-stu-id="d48f7-121">Example</span></span>  
 <span data-ttu-id="d48f7-122">最後，建立並新增頁尾資料列，然後設定格式。</span><span class="sxs-lookup"><span data-stu-id="d48f7-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="d48f7-123">如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。</span><span class="sxs-lookup"><span data-stu-id="d48f7-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="d48f7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d48f7-124">See also</span></span>

- [<span data-ttu-id="d48f7-125">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="d48f7-125">Table Overview</span></span>](table-overview.md)
