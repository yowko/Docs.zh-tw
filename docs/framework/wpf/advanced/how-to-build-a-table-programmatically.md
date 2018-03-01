---
title: "如何：以程式設計的方式建置資料表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fca6a304ea12dd90a71f8718fed5f1595f4cd4b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-table-programmatically"></a>如何：以程式設計的方式建置資料表
下列範例顯示如何以程式設計方式建立<xref:System.Windows.Documents.Table>並填入內容。 資料表的內容分配到五個資料列 (由<xref:System.Windows.Documents.TableRow>所包含的物件<xref:System.Windows.Documents.Table.RowGroups%2A>物件) 和六個資料行 (由<xref:System.Windows.Documents.TableColumn>物件)。 資料列可用於不同的顯示用途，包括用來為整個表格加上標題的標題資料列、用來說明表格中資料之資料行的標頭資料列，以及含有摘要資訊的頁尾資料列。  請注意，「標題」、「標頭」和「頁尾」資料列的概念不是表格固有的；這些只是具有不同特性的資料列。 資料表資料格包含實際的內容，其中可包含的文字、 影像或幾乎任何其他[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]項目。  
  
## <a name="example"></a>範例  
 首先，<xref:System.Windows.Documents.FlowDocument>建立主機<xref:System.Windows.Documents.Table>，和新<xref:System.Windows.Documents.Table>已建立並加入至內容<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>範例  
 接下來的六個<xref:System.Windows.Documents.TableColumn>物件會建立並加入至資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合中具有某些所套用的格式。  
  
> [!NOTE]
>  請注意，資料表的<xref:System.Windows.Documents.Table.Columns%2A>集合會使用標準的以零為起始索引。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>範例  
 接下來，建立標題資料列，並新增至已套用某些格式的資料表。  標題資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>範例  
 接著，建立標頭資料列並新增至表格，然後在標頭資料列中建立儲存格並填入內容。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>範例  
 接下來，建立資料的資料列並新增至資料表，然後在此資料列中建立儲存格並填入內容。  建置此資料列類似於建置標頭資料列，但套用的格式稍有不同。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>範例  
 最後，建立並新增頁尾資料列，然後設定格式。  如同標題資料列，頁尾資料列會在資料表中包含跨越所有六個資料行的單一儲存格。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>請參閱  
 [資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)
