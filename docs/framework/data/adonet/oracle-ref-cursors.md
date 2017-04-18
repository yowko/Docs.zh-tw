---
title: "Oracle REF CURSOR | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Oracle REF CURSOR
Oracle 的 .NET Framework 資料提供者支援 Oracle **REF CURSOR** 資料型別。  透過資料提供者使用 Oracle REF CURSOR 時，您應考量下列行為。  
  
> [!NOTE]
>  某些行為與 Oracle 的 Microsoft OLE DB 提供者 \(MSDAORA\) 的行為不同。  
  
-   基於效能方面的原因，除非您明確指定，否則 Oracle 的資料提供者不會如 MSDAORA 一樣，自動繫結 **REF CURSOR** 資料型別。  
  
-   該資料提供者不支援任何 ODBC 逸出序列，包括用來指定 REF CURSOR 參數的 {resultset} 逸出。  
  
-   若要執行傳回 REF CURSOR 的預存程序，您必須以 **Cursor** 的 <xref:System.Data.OracleClient.OracleType> 及 **Output** 的 <xref:System.Data.OracleClient.OracleParameter.Direction%2A>，定義 <xref:System.Data.OracleClient.OracleParameterCollection> 中的參數。  資料提供者僅支援將 REF CURSOR 繫結為輸出參數。  提供者不支援 REF CURSOR 做為輸入參數。  
  
-   不支援從參數值取得 <xref:System.Data.OracleClient.OracleDataReader>。  命令執行後，值的型別為 <xref:System.DBNull>。  
  
-   使用 REF CURSOR \(例如，呼叫 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> 時\) 的唯一 **CommandBehavior** 列舉型別值為 **CloseConnection**；忽略其他所有值。  
  
-   **OracleDataReader** 中 REF CURSOR 的順序取決於 **OracleParameterCollection** 中參數的順序。  忽略 <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> 屬性。  
  
-   不支援 PL\/SQL **TABLE** 資料型別。  然而，REF CURSOR 更有效率。  如果您必須使用 **TABLE** 資料型別，請搭配使用 OLE DB .NET 資料提供者與 MSDAORA。  
  
## 在本節中  
 [REF CURSOR 範例](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 包含示範如何使用 REF CURSOR 的三個範例。  
  
 [OracleDataReader 中的 REF CURSOR 參數](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 示範如何執行傳回 REF CURSOR 參數的 PL\/SQL 預存程序，並以 **OracleDataReader** 讀取值。  
  
 [使用 OracleDataReader 從多個 REF CURSOR 擷取資料](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 示範如何執行傳回兩個 REF CURSOR 參數的 PL\/SQL 預存程序，並使用 **OracleDataReader** 讀取值。  
  
 [使用一個或多個 REF CURSOR 填入資料集](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 示範如何執行傳回兩個 REF CURSOR 參數的 PL\/SQL 預存程序，並使用傳回的資料列填入 <xref:System.Data.DataSet>。  
  
## 請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)