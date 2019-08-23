---
title: 作法：透過 Columns 屬性管理資料表的資料行
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
ms.openlocfilehash: 18a26c76688ebf668293cb1254404d6d2cf15208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913597"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a>HOW TO：透過 Columns 屬性管理資料表的資料行
這個範例示範一些較常見的作業, 可以透過<xref:System.Windows.Documents.Table.Columns%2A>屬性在資料表的資料行上執行。  
  
## <a name="example"></a>範例  
 下列範例會建立新的資料表, 然後使用<xref:System.Windows.Documents.TableColumnCollection.Add%2A>方法將資料行加入至資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a>範例  
 下列範例會插入新<xref:System.Windows.Documents.TableColumn>的。  新的資料行會插入索引位置 0, 使其成為資料表中的第一個新資料行。  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableColumnCollection>集合會使用標準的以零為起始的索引。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a>範例  
 下列範例會針對<xref:System.Windows.Documents.TableColumnCollection>集合中的資料行存取一些任意屬性, 依索引來參考特定的資料行。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a>範例  
 下列範例會取得資料表目前裝載的資料行數目。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a>範例  
 下列範例會以傳址方式移除特定的資料行。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a>範例  
 下列範例會依索引移除特定的資料行。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a>範例  
 下列範例會從資料表的資料行集合中移除所有資料行。  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a>另請參閱

- [資料表概觀](table-overview.md)
- [使用 XAML 定義表格](how-to-define-a-table-with-xaml.md)
- [以程式設計的方式建置資料表](how-to-build-a-table-programmatically.md)
- [透過 RowGroups 屬性管理表格的資料列群組](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [透過 Blocks 屬性管理 FlowDocument](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [透過 RowGroups 屬性管理表格的資料列群組](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
