---
title: HOW TO：透過 Columns 屬性管理資料表的資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
ms.openlocfilehash: d379d1a98bff614ff9e16cdd340bb69644988743
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078417"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="04b97-102">HOW TO：透過 Columns 屬性管理資料表的資料行</span><span class="sxs-lookup"><span data-stu-id="04b97-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="04b97-103">此範例示範一些較常見的作業對資料表的資料行<xref:System.Windows.Documents.Table.Columns%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="04b97-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04b97-104">範例</span><span class="sxs-lookup"><span data-stu-id="04b97-104">Example</span></span>  
 <span data-ttu-id="04b97-105">下列範例會建立新的資料表，並接著會使用<xref:System.Windows.Documents.TableColumnCollection.Add%2A>方法，以將資料行加入資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="04b97-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="04b97-106">範例</span><span class="sxs-lookup"><span data-stu-id="04b97-106">Example</span></span>  
 <span data-ttu-id="04b97-107">下列範例會插入新<xref:System.Windows.Documents.TableColumn>。</span><span class="sxs-lookup"><span data-stu-id="04b97-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="04b97-108">新的資料行是索引位置插入 0，使得它成為新的第一個資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="04b97-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04b97-109"><xref:System.Windows.Documents.TableColumnCollection>集合會使用標準的以零為起始索引。</span><span class="sxs-lookup"><span data-stu-id="04b97-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="04b97-110">範例</span><span class="sxs-lookup"><span data-stu-id="04b97-110">Example</span></span>  
 <span data-ttu-id="04b97-111">下列範例會存取某些中的資料行上的任何屬性<xref:System.Windows.Documents.TableColumnCollection>集合參考特定的資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="04b97-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="04b97-112">範例</span><span class="sxs-lookup"><span data-stu-id="04b97-112">Example</span></span>  
 <span data-ttu-id="04b97-113">下列範例會取得目前資料表所裝載的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="04b97-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="04b97-114">範例</span><span class="sxs-lookup"><span data-stu-id="04b97-114">Example</span></span>  
 <span data-ttu-id="04b97-115">下列範例會移除特定的資料行的參考。</span><span class="sxs-lookup"><span data-stu-id="04b97-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="04b97-116">範例</span><span class="sxs-lookup"><span data-stu-id="04b97-116">Example</span></span>  
 <span data-ttu-id="04b97-117">下列範例會移除特定的資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="04b97-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="04b97-118">範例</span><span class="sxs-lookup"><span data-stu-id="04b97-118">Example</span></span>  
 <span data-ttu-id="04b97-119">下列範例會移除資料表的資料行集合中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="04b97-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="04b97-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04b97-120">See also</span></span>

- [<span data-ttu-id="04b97-121">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="04b97-121">Table Overview</span></span>](table-overview.md)
- [<span data-ttu-id="04b97-122">使用 XAML 定義表格</span><span class="sxs-lookup"><span data-stu-id="04b97-122">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="04b97-123">以程式設計的方式建置資料表</span><span class="sxs-lookup"><span data-stu-id="04b97-123">Build a Table Programmatically</span></span>](how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="04b97-124">透過 RowGroups 屬性管理表格的資料列群組</span><span class="sxs-lookup"><span data-stu-id="04b97-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="04b97-125">透過 Blocks 屬性管理 FlowDocument</span><span class="sxs-lookup"><span data-stu-id="04b97-125">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="04b97-126">透過 RowGroups 屬性管理表格的資料列群組</span><span class="sxs-lookup"><span data-stu-id="04b97-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
