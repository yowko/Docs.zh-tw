---
title: 適用於 Entity Framework 的 SqlClient 已知問題
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 5c500a61a00914df7b106b7e89485921123e56ec
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489543"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>適用於 Entity Framework 的 SqlClient 已知問題
本節說明與 .NET Framework Data Provider for SQL Server (SqlClient) 相關的已知問題。  
  
## <a name="trailing-spaces-in-string-functions"></a>字串函式中的尾端空白  
 SQL Server 會忽略字串值中的尾端空白。 因此，在字串中傳遞尾端空白會導致無法預期的結果，甚至產生錯誤。  
  
 如果您需要在字串中的尾端空格，您應該考慮附加空白字元結尾，使 SQL Server 不會修剪的字串。 如果尾端空白是不必要的，則應該在查詢管線中傳遞前先行修剪掉。  
  
## <a name="right-function"></a>RIGHT 函式  
 如果將非 `null` 值傳遞做為第一個引數並將 0 傳遞做為第二個引數，成為 `RIGHT(nvarchar(max)`, 0`)` 或 `RIGHT(varchar(max)`, 0`)`，則會傳回 `NULL` 值，而非 `empty` 字串。  
  
## <a name="cross-and-outer-apply-operators"></a>CROSS 和 OUTER APPLY 運算子  
 CROSS 和 OUTER APPLY 運算子是在 [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] 中引入的。 在某些案例中，查詢管線可能產生含有 CROSS APPLY 和 (或) OUTER APPLY 運算子的 Transact-SQL 陳述式。 因為有些後端提供者，包括 SQL Server 版本早於[!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]，不支援這些運算子，這些後端提供者無法執行這類查詢。  
  
 下列是可能會導致輸出查詢中出現 CROSS APPLY 和 (或) OUTER APPLY 運算子的部分典型案例：  
  
- 具有分頁的相互關聯子查詢。  
  
- 相互關聯子查詢或巡覽產生的集合上的 `AnyElement`。  
  
- 使用接受元素選擇器的群組方法的 LINQ 查詢。  
  
- 當中有明確指定 CROSS APPLY 或 OUTER APPLY 的查詢。  
  
- 具有 DEREF 建構對 REF 建構的查詢。  
  
## <a name="skip-operator"></a>SKIP 運算子  
 如果您使用[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]，SKIP 搭配 ORDER BY 使用非索引鍵資料行上可能會傳回不正確的結果。 如果非索引鍵資料行中有重複的資料，可能會略過超過所指定數目的資料行。 這是因為 SKIP 針對 [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]轉譯的方式所造成的。 例如，在下列查詢中，五個以上的資料列可能會略過如果`E.NonKeyColumn`有重複的值：  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>以正確的 SQL Server 版本為目標  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]目標中指定的 SQL Server 版本為基礎的 TRANSACT-SQL 查詢`ProviderManifestToken`儲存模型 (.ssdl) 檔案中的結構描述項目的屬性。 這個版本可能會因您所連接的 SQL Server 實際版本而有所不同。 例如，如果您使用 SQL Server 2005，但您`ProviderManifestToken`屬性設為 2008年，產生的 TRANSACT-SQL 查詢可能不會在伺服器上執行。 例如，使用 SQL Server 2008 中導入新的日期時間類型的查詢將不會執行較舊版本的 SQL server。 如果您使用 SQL Server 2005，但您`ProviderManifestToken`屬性設為 2000年，可能會較不最佳化產生的 TRANSACT-SQL 查詢，或您可能會收到例外狀況指出不支援的查詢。 如需詳細資訊，請參閱本主題前面的「CROSS 和 OUTER APPLY 運算子」一節。  
  
 某些資料庫行為取決於資料庫上設定的相容性層級。 如果您`ProviderManifestToken`屬性設為 2005年和 SQL Server 版本是 2005，但資料庫的相容性層級設定為"80"(SQL Server 2000)，產生的 TRANSACT-SQL 將挑選作為目標 SQL Server 2005，但可能不會如預期般運作，因為執行相容性層級設定。 例如，當 ORDER BY 清單中資料行名稱與選擇器中資料行名稱相符合時，則可能會遺失排序資訊。  
  
## <a name="nested-queries-in-projection"></a>投影中的巢狀查詢  
 投影子句中的巢狀查詢可能會在伺服器上轉譯成笛卡兒乘積 (Cartesian Product) 查詢。 在包括 SLQ Server 的某些後端伺服器上，這會導致 TempDB 資料表變得很大。 這樣會降低伺服器的效能。  
  
 下列是投影子句中巢狀查詢的範例：  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>伺服器產生的 GUID 識別值  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 支援伺服器產生的 GUID 識別值，但是提供者必須支援在資插入資料列之後，傳回伺服器產生的識別值。 從 SQL Server 2005 開始，您可以傳回伺服器產生的 GUID 型別在 SQL Server 資料庫裡[OUTPUT 子句](https://go.microsoft.com/fwlink/?LinkId=169400)。  
  
## <a name="see-also"></a>另請參閱

- [適用於 Entity Framework 的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
- [LINQ to Entities 中的已知問題和考量](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
