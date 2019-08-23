---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7c6b326b15a2af58da9206adf28070e57fec600c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963506"
---
# <a name="oracle-ref-cursors"></a>Oracle REF CURSOR
Oracle 的 .NET Framework Data Provider 支援 Oracle **REF CURSOR**資料類型。 透過資料提供者使用 Oracle REF CURSOR 時，您應考量下列行為。  
  
> [!NOTE]
> 某些行為與 Oracle 的 Microsoft OLE DB 提供者 (MSDAORA) 的行為不同。  
  
- 基於效能的考慮, 除非您明確指定, 否則 Oracle 的 Data Provider 不會自動系結**REF CURSOR**資料類型 (如 MSDAORA 所示)。  
  
- 該資料提供者不支援任何 ODBC 逸出序列，包括用來指定 REF CURSOR 參數的 {resultset} 逸出。  
  
- 若要執行可傳回 REF 資料指標的預存程式<xref:System.Data.OracleClient.OracleParameterCollection> , 您必須<xref:System.Data.OracleClient.OracleType>使用資料**指標**的和<xref:System.Data.OracleClient.OracleParameter.Direction%2A> **輸出**的來定義中的參數。 資料提供者僅支援將 REF CURSOR 繫結為輸出參數。 提供者不支援 REF CURSOR 做為輸入參數。  
  
- 不支援從參數值取得 <xref:System.Data.OracleClient.OracleDataReader>。 命令執行後，值的型別為 <xref:System.DBNull>。  
  
- 唯一可搭配 REF 資料指標使用的**CommandBehavior**列舉值 (例如, 呼叫<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>時) 為**CloseConnection**; 所有其他專案都會被忽略。  
  
- **OracleDataReader**中 REF 資料指標的順序取決於**OracleParameterCollection**中參數的順序。 忽略 <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> 屬性。  
  
- 不支援 PL/SQL**資料表**資料類型。 然而，REF CURSOR 更有效率。 如果您必須使用**資料表**資料類型, 請使用 OLE DB .net DATA PROVIDER 搭配 MSDAORA。  
  
## <a name="in-this-section"></a>本節內容  
 [REF CURSOR 範例](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 包含示範如何使用 REF CURSOR 的三個範例。  
  
 [OracleDataReader 中的 REF CURSOR 參數](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 示範如何執行會傳回 REF CURSOR 參數的 PL/SQL 預存程式, 並以**OracleDataReader**的形式讀取該值。  
  
 [使用 OracleDataReader 從多個 REF CURSOR 擷取資料](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 示範如何執行會傳回兩個 REF CURSOR 參數的 PL/SQL 預存程式, 並使用**OracleDataReader**來讀取值。  
  
 [使用一或多個 REF CURSOR 填入資料集](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 示範如何執行傳回兩個 REF CURSOR 參數的 PL/SQL 預存程序，並使用傳回的資料列填入 <xref:System.Data.DataSet>。  
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
