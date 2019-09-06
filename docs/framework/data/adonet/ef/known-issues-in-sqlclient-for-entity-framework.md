---
title: 適用於 Entity Framework 的 SqlClient 已知問題
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 5c0b7c32e00a0cc90367a559a41f5a7ab59a33a4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251386"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>適用於 Entity Framework 的 SqlClient 已知問題
本節說明與 .NET Framework Data Provider for SQL Server (SqlClient) 相關的已知問題。  
  
## <a name="trailing-spaces-in-string-functions"></a>字串函式中的尾端空白  
 SQL Server 會忽略字串值中的尾端空格。 因此，在字串中傳遞尾端空白會導致無法預期的結果，甚至產生錯誤。  
  
 如果您的字串中必須有尾端空格, 您應該考慮在結尾附加空白字元, 讓 SQL Server 不會修剪字串。 如果尾端空白是不必要的，則應該在查詢管線中傳遞前先行修剪掉。  
  
## <a name="right-function"></a>RIGHT 函式  
 如果將非 `null` 值傳遞做為第一個引數並將 0 傳遞做為第二個引數，成為 `RIGHT(nvarchar(max)`, 0`)` 或 `RIGHT(varchar(max)`, 0`)`，則會傳回 `NULL` 值，而非 `empty` 字串。  
  
## <a name="cross-and-outer-apply-operators"></a>CROSS 和 OUTER APPLY 運算子  
 CROSS 和 OUTER APPLY 運算子是在 SQL Server 2005 中引進。 在某些案例中，查詢管線可能產生含有 CROSS APPLY 和 (或) OUTER APPLY 運算子的 Transact-SQL 陳述式。 因為有些後端提供者 (包括早于 SQL Server 2005 的 SQL Server 版本) 不支援這些運算子, 所以無法在這些後端提供者上執行這類查詢。  
  
 下列是可能會導致輸出查詢中出現 CROSS APPLY 和 (或) OUTER APPLY 運算子的部分典型案例：  
  
- 具有分頁的相互關聯子查詢。  
  
- 相互關聯子查詢或巡覽產生的集合上的 `AnyElement`。  
  
- 使用接受元素選擇器的群組方法的 LINQ 查詢。  
  
- 當中有明確指定 CROSS APPLY 或 OUTER APPLY 的查詢。  
  
- 具有 DEREF 建構對 REF 建構的查詢。  
  
## <a name="skip-operator"></a>SKIP 運算子  
 如果您使用 SQL Server 2000, 則在非索引鍵資料行上使用 SKIP 搭配 ORDER BY 可能會傳回不正確的結果。 如果非索引鍵資料行中有重複的資料，可能會略過超過所指定數目的資料行。 這是因為 SQL Server 2000 的略過轉譯方式所致。 例如, 在下列查詢中, 如果有重複的值, 則`E.NonKeyColumn`可能會略過超過五個數據列:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>以正確的 SQL Server 版本為目標  
 會根據儲存模型 (ssdl) 檔案中 Schema 元素的`ProviderManifestToken`屬性所指定的 SQL Server 版本, 以 transact-SQL 查詢為目標。[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 這個版本可能會因您所連接的 SQL Server 實際版本而有所不同。 例如, 如果您使用 SQL Server 2005, 但您`ProviderManifestToken`的屬性設定為 2008, 則產生的 transact-SQL 查詢可能無法在伺服器上執行。 例如, 使用在 SQL Server 2008 中引進之新日期時間類型的查詢, 將不會在舊版的 SQL Server 上執行。 如果您使用 SQL Server 2005, 但您`ProviderManifestToken`的屬性設定為 2000, 則產生的 transact-SQL 查詢可能較不優化, 或者您可能會收到例外狀況, 指出不支援該查詢。 如需詳細資訊，請參閱本主題前面的「CROSS 和 OUTER APPLY 運算子」一節。  
  
 某些資料庫行為取決於資料庫上設定的相容性層級。 如果您`ProviderManifestToken`的屬性設定為 2005, 而您的 SQL Server 版本是 2005, 但資料庫的相容性層級設定為 "80" (SQL Server 2000), 則產生的 transact-sql 將以 SQL Server 的2005為目標, 但可能不會如預期般執行, 因為相容性層級設定。 例如，當 ORDER BY 清單中資料行名稱與選擇器中資料行名稱相符合時，則可能會遺失排序資訊。  
  
## <a name="nested-queries-in-projection"></a>投影中的巢狀查詢  
 投影子句中的巢狀查詢可能會在伺服器上轉譯成笛卡兒乘積 (Cartesian Product) 查詢。 在某些後端伺服器 (包括 SLQ 伺服器) 上, 這可能會導致 TempDB 資料表變得相當大。 這樣會降低伺服器的效能。  
  
 下列是投影子句中巢狀查詢的範例：  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>伺服器產生的 GUID 識別值  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 支援伺服器產生的 GUID 識別值，但是提供者必須支援在資插入資料列之後，傳回伺服器產生的識別值。 從 SQL Server 2005 開始, 您可以透過[OUTPUT 子句](https://go.microsoft.com/fwlink/?LinkId=169400), 在 SQL Server 資料庫中傳回伺服器產生的 GUID 型別。  
  
## <a name="see-also"></a>另請參閱

- [適用於 Entity Framework 的 SqlClient](sqlclient-for-the-entity-framework.md)
- [LINQ to Entities 中的已知問題和考量](./language-reference/known-issues-and-considerations-in-linq-to-entities.md)
