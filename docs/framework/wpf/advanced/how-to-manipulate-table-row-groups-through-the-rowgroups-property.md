---
title: HOW TO：透過 RowGroups 屬性管理資料表的資料列群組
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
ms.openlocfilehash: 6c1e3318afeb8147e96dc3abc5417f2c29509d13
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274894"
---
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="f25bf-102">HOW TO：透過 RowGroups 屬性管理資料表的資料列群組</span><span class="sxs-lookup"><span data-stu-id="f25bf-102">How to: Manipulate a Table's Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="f25bf-103">此範例示範一些較常見的作業對資料表的資料列群組，透過<xref:System.Windows.Documents.Table.RowGroups%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f25bf-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f25bf-104">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-104">Example</span></span>  
 <span data-ttu-id="f25bf-105">下列範例會建立新的資料表，並接著會使用<xref:System.Windows.Documents.TableRowGroupCollection.Add%2A>方法，以將資料行加入資料表的<xref:System.Windows.Documents.Table.RowGroups%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="f25bf-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-106">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-106">Example</span></span>  
 <span data-ttu-id="f25bf-107">下列範例會插入新<xref:System.Windows.Documents.TableRowGroup>。</span><span class="sxs-lookup"><span data-stu-id="f25bf-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="f25bf-108">新的資料行的索引位置 0，因此新的第一個資料列插入資料表中的群組。</span><span class="sxs-lookup"><span data-stu-id="f25bf-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f25bf-109"><xref:System.Windows.Documents.TableRowGroupCollection>集合會使用標準的以零為起始索引。</span><span class="sxs-lookup"><span data-stu-id="f25bf-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-110">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-110">Example</span></span>  
 <span data-ttu-id="f25bf-111">下列範例會將數個資料列加入至特定<xref:System.Windows.Documents.TableRowGroup>（由索引指定） 資料表中。</span><span class="sxs-lookup"><span data-stu-id="f25bf-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-112">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-112">Example</span></span>  
 <span data-ttu-id="f25bf-113">下列範例會存取某些資料表中的第一個資料列群組中的資料列上的任何屬性。</span><span class="sxs-lookup"><span data-stu-id="f25bf-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-114">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-114">Example</span></span>  
 <span data-ttu-id="f25bf-115">下列範例會將數個資料格特定<xref:System.Windows.Documents.TableRow>（由索引指定） 資料表中。</span><span class="sxs-lookup"><span data-stu-id="f25bf-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-116">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-116">Example</span></span>  
 <span data-ttu-id="f25bf-117">下列範例會存取一些任意的方法和屬性中第一個資料列群組中的第一個資料列的資料格。</span><span class="sxs-lookup"><span data-stu-id="f25bf-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-118">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-118">Example</span></span>  
 <span data-ttu-id="f25bf-119">下列範例會傳回的數目<xref:System.Windows.Documents.TableRowGroup>資料表所裝載的項目。</span><span class="sxs-lookup"><span data-stu-id="f25bf-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-120">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-120">Example</span></span>  
 <span data-ttu-id="f25bf-121">下列範例會移除特定的資料列群組的參考。</span><span class="sxs-lookup"><span data-stu-id="f25bf-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-122">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-122">Example</span></span>  
 <span data-ttu-id="f25bf-123">下列範例會移除特定的資料列群組的索引。</span><span class="sxs-lookup"><span data-stu-id="f25bf-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="f25bf-124">範例</span><span class="sxs-lookup"><span data-stu-id="f25bf-124">Example</span></span>  
 <span data-ttu-id="f25bf-125">下列範例會移除資料表的資料列群組集合中的所有資料列群組。</span><span class="sxs-lookup"><span data-stu-id="f25bf-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="f25bf-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f25bf-126">See also</span></span>
- [<span data-ttu-id="f25bf-127">操作說明：管理非固定格式內容項目，透過 Inlines 屬性</span><span class="sxs-lookup"><span data-stu-id="f25bf-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="f25bf-128">透過 Blocks 屬性管理 FlowDocument</span><span class="sxs-lookup"><span data-stu-id="f25bf-128">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="f25bf-129">透過 Columns 屬性管理表格的資料行</span><span class="sxs-lookup"><span data-stu-id="f25bf-129">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)
