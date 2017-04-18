---
title: "如何：以程式設計的方式建置資料表 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "建立, 資料表 (以程式設計方式)"
  - "文件, 以程式設計方式建立資料表"
  - "資料表, 以程式設計方式建立"
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：以程式設計的方式建置資料表
下列範例顯示如何以程式設計的方式建立 <xref:System.Windows.Documents.Table> 並為其填入內容。  資料表的內容會分配到五個資料列 \(以 <xref:System.Windows.Documents.Table.RowGroups%2A> 物件中所含的 <xref:System.Windows.Documents.TableRow> 物件表示\) 及六個資料行 \(以 <xref:System.Windows.Documents.TableColumn> 物件表示\) 中。  這些資料列分別用於不同的顯示用途，包括為整個資料表下標的標題資料列、用以說明資料表中各資料行的頁首資料列，以及具有摘要資訊的頁尾資料列。  請注意，「標題」、「頁首」與「頁尾」等資料列的概念並非資料表原本所固有，它們只是具有不同特性的資料列。  資料表儲存格含有實際的內容，其中可包含文字、影像或其他幾乎所有的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 項目。  
  
## 範例  
 首先，建立 <xref:System.Windows.Documents.FlowDocument> 以裝載 <xref:System.Windows.Documents.Table>，然後建立新的 <xref:System.Windows.Documents.Table> 並將其加入至 <xref:System.Windows.Documents.FlowDocument> 的內容中。  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## 範例  
 接著，建立六個 <xref:System.Windows.Documents.TableColumn> 物件，並將其加入至資料表的 <xref:System.Windows.Documents.Table.Columns%2A> 集合中，並為其套用某格式。  
  
> [!NOTE]
>  請注意，資料表的 <xref:System.Windows.Documents.Table.Columns%2A> 集合使用以零起始的標準索引。  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## 範例  
 接下來建立標題資料列，並將其加入至資料表中並套用某格式。  標題資料列包含單一儲存格，但擴展至資料表中全部六個資料行。  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## 範例  
 接著建立頁首資料列，並將其加入至資料表中，頁首資料列中會建立儲存格，並填入內容。  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## 範例  
 接著建立資料的資料列，並將其加入至資料表中，此資料列中會建立儲存格，並填入內容。  建置此資料列與建置頁首資料列相似，差別在於套用的格式略有不同。  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## 範例  
 最後建立頁尾資料列，並將其加入與格式化。  與標題資料列相同，頁尾也包含單一儲存格但擴展至資料表中全部六個資料行。  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## 請參閱  
 [資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)