---
title: "如何： 操作資料表 &#39; s 屬性資料行的資料行"
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
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d0f15339b829335798d7ee21dcc90b81cb536cf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a><span data-ttu-id="8055b-102">如何： 操作資料表 &#39; s 屬性資料行的資料行</span><span class="sxs-lookup"><span data-stu-id="8055b-102">How to: Manipulate a Table&#39;s Columns through the Columns Property</span></span>
<span data-ttu-id="8055b-103">這個範例會示範一些較常見可以透過資料表的資料行執行的運算<xref:System.Windows.Documents.Table.Columns%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="8055b-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8055b-104">範例</span><span class="sxs-lookup"><span data-stu-id="8055b-104">Example</span></span>  
 <span data-ttu-id="8055b-105">下列範例會建立新的資料表，然後再使用<xref:System.Windows.Documents.TableColumnCollection.Add%2A>方法，以將資料行加入資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="8055b-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="8055b-106">範例</span><span class="sxs-lookup"><span data-stu-id="8055b-106">Example</span></span>  
 <span data-ttu-id="8055b-107">下列範例會將新<xref:System.Windows.Documents.TableColumn>。</span><span class="sxs-lookup"><span data-stu-id="8055b-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="8055b-108">索引位置 0，因此新的第一個資料行的資料表中插入新的資料行。</span><span class="sxs-lookup"><span data-stu-id="8055b-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8055b-109"><xref:System.Windows.Documents.TableColumnCollection>集合會使用標準的以零為起始索引。</span><span class="sxs-lookup"><span data-stu-id="8055b-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="8055b-110">範例</span><span class="sxs-lookup"><span data-stu-id="8055b-110">Example</span></span>  
 <span data-ttu-id="8055b-111">下列範例會存取一些任意數目的屬性中的資料行<xref:System.Windows.Documents.TableColumnCollection>集合參考特定資料行索引。</span><span class="sxs-lookup"><span data-stu-id="8055b-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="8055b-112">範例</span><span class="sxs-lookup"><span data-stu-id="8055b-112">Example</span></span>  
 <span data-ttu-id="8055b-113">下列範例會取得目前資料表所裝載的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="8055b-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="8055b-114">範例</span><span class="sxs-lookup"><span data-stu-id="8055b-114">Example</span></span>  
 <span data-ttu-id="8055b-115">下列範例會移除特定的資料行的參考。</span><span class="sxs-lookup"><span data-stu-id="8055b-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="8055b-116">範例</span><span class="sxs-lookup"><span data-stu-id="8055b-116">Example</span></span>  
 <span data-ttu-id="8055b-117">下列範例會移除特定的資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="8055b-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="8055b-118">範例</span><span class="sxs-lookup"><span data-stu-id="8055b-118">Example</span></span>  
 <span data-ttu-id="8055b-119">下列範例會移除資料表的資料行集合中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="8055b-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="8055b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8055b-120">See Also</span></span>  
 [<span data-ttu-id="8055b-121">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="8055b-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [<span data-ttu-id="8055b-122">使用 XAML 定義表格</span><span class="sxs-lookup"><span data-stu-id="8055b-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="8055b-123">以程式設計的方式建置資料表</span><span class="sxs-lookup"><span data-stu-id="8055b-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [<span data-ttu-id="8055b-124">透過 RowGroups 屬性管理表格的資料列群組</span><span class="sxs-lookup"><span data-stu-id="8055b-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="8055b-125">透過 Blocks 屬性管理 FlowDocument</span><span class="sxs-lookup"><span data-stu-id="8055b-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="8055b-126">透過 RowGroups 屬性管理表格的資料列群組</span><span class="sxs-lookup"><span data-stu-id="8055b-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
