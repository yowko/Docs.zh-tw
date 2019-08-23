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
# <a name="how-to-build-a-table-programmatically"></a>作法：以程式設計方式建置資料表
下列範例示範如何以程式設計方式建立<xref:System.Windows.Documents.Table> , 並在其中填入內容。 資料表的內容會分配為五個數據列 (以<xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.Table.RowGroups%2A>物件所包含的物件表示) 和<xref:System.Windows.Documents.TableColumn>六個數據行 (以物件表示)。 資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。  請注意，「標題」、「標頭」和「頁尾」資料列的概念不是表格固有的；這些只是具有不同特性的資料列。 資料表單元格包含實際內容, 其可由文字、影像或幾乎任何其他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]元素組成。  
  
## <a name="example"></a>範例  
 首先, <xref:System.Windows.Documents.FlowDocument>會建立來<xref:System.Windows.Documents.Table>裝載, 並<xref:System.Windows.Documents.FlowDocument>建立新<xref:System.Windows.Documents.Table>的, 並將其新增至的內容。  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>範例  
 接下來, <xref:System.Windows.Documents.TableColumn>會建立六個物件, 並將其<xref:System.Windows.Documents.Table.Columns%2A>新增至資料表的集合, 並套用一些格式。  
  
> [!NOTE]
> 請注意, 資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合會使用標準的以零為起始的索引。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>範例  
 接下來，建立標題資料列，並新增至已套用某些格式的資料表。  標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>範例  
 接著，建立標頭資料列並新增至表格，然後在標頭資料列中建立儲存格並填入內容。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>範例  
 接下來，建立資料的資料列並新增至資料表，然後在此資料列中建立儲存格並填入內容。  建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>範例  
 最後，建立並新增頁尾資料列，然後設定格式。  如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>另請參閱

- [資料表概觀](table-overview.md)
