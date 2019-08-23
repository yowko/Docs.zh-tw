---
title: 作法：透過 RowGroups 屬性管理資料表的資料列群組
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- row groups [WPF], manipulating through RowGroups property
- RowGroups property [WPF], manipulating row groups
- documents [WPF], manipulating row groups through RowGroups property
- properties [WPF], RowGroups [WPF], manipulating row groups
ms.assetid: ea61440f-08ae-44ed-b314-5716aaaae3ed
ms.openlocfilehash: 195920af64888bd3671b45befc0fe4cde463ae7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913551"
---
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="46fdb-102">作法：透過 RowGroups 屬性管理資料表的資料列群組</span><span class="sxs-lookup"><span data-stu-id="46fdb-102">How to: Manipulate a Table's Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="46fdb-103">這個範例示範一些較常見的作業, 可以透過<xref:System.Windows.Documents.Table.RowGroups%2A>屬性在資料表的資料列群組上執行。</span><span class="sxs-lookup"><span data-stu-id="46fdb-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46fdb-104">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-104">Example</span></span>  
 <span data-ttu-id="46fdb-105">下列範例會建立新的資料表, 然後使用<xref:System.Windows.Documents.TableRowGroupCollection.Add%2A>方法將資料行加入至資料表的<xref:System.Windows.Documents.Table.RowGroups%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="46fdb-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-106">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-106">Example</span></span>  
 <span data-ttu-id="46fdb-107">下列範例會插入新<xref:System.Windows.Documents.TableRowGroup>的。</span><span class="sxs-lookup"><span data-stu-id="46fdb-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="46fdb-108">新的資料行會插入索引位置 0, 使其成為資料表中的新第一個資料列群組。</span><span class="sxs-lookup"><span data-stu-id="46fdb-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46fdb-109"><xref:System.Windows.Documents.TableRowGroupCollection>集合會使用標準的以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="46fdb-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-110">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-110">Example</span></span>  
 <span data-ttu-id="46fdb-111">下列範例會將數個數據列加入<xref:System.Windows.Documents.TableRowGroup>資料表中的特定 (由索引指定)。</span><span class="sxs-lookup"><span data-stu-id="46fdb-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-112">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-112">Example</span></span>  
 <span data-ttu-id="46fdb-113">下列範例會存取資料表中第一個資料列群組的資料列上的一些任意屬性。</span><span class="sxs-lookup"><span data-stu-id="46fdb-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-114">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-114">Example</span></span>  
 <span data-ttu-id="46fdb-115">下列範例會將數個數據格加入<xref:System.Windows.Documents.TableRow>資料表中的特定 (由索引指定)。</span><span class="sxs-lookup"><span data-stu-id="46fdb-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-116">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-116">Example</span></span>  
 <span data-ttu-id="46fdb-117">下列範例會存取第一個資料列群組中第一個資料列的資料格上的一些任意方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="46fdb-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-118">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-118">Example</span></span>  
 <span data-ttu-id="46fdb-119">下列範例會傳回資料表所裝載<xref:System.Windows.Documents.TableRowGroup>的元素數目。</span><span class="sxs-lookup"><span data-stu-id="46fdb-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-120">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-120">Example</span></span>  
 <span data-ttu-id="46fdb-121">下列範例會以傳址方式移除特定的資料列群組。</span><span class="sxs-lookup"><span data-stu-id="46fdb-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-122">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-122">Example</span></span>  
 <span data-ttu-id="46fdb-123">下列範例會依索引移除特定的資料列群組。</span><span class="sxs-lookup"><span data-stu-id="46fdb-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="46fdb-124">範例</span><span class="sxs-lookup"><span data-stu-id="46fdb-124">Example</span></span>  
 <span data-ttu-id="46fdb-125">下列範例會從資料表的資料列群組集合中移除所有資料列群組。</span><span class="sxs-lookup"><span data-stu-id="46fdb-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="46fdb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46fdb-126">See also</span></span>

- [<span data-ttu-id="46fdb-127">操作說明：透過內嵌屬性管理非固定格式內容元素</span><span class="sxs-lookup"><span data-stu-id="46fdb-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="46fdb-128">透過 Blocks 屬性管理 FlowDocument</span><span class="sxs-lookup"><span data-stu-id="46fdb-128">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="46fdb-129">透過 Columns 屬性管理表格的資料行</span><span class="sxs-lookup"><span data-stu-id="46fdb-129">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
