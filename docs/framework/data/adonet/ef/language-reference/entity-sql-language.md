---
title: Entity SQL 語言
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 09ec1a5518ec0847b54394449f32b3068c811577
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140929"
---
# <a name="entity-sql-language"></a>Entity SQL 語言
Entity SQL 是與儲存體無關的查詢語言，與 SQL 類似。 Entity SQL 可讓您查詢實體資料 (無論以物件形式或在表格式資料表中)。 在下列情況下，您可以考慮使用 Entity SQL：  
  
-   必須在執行階段動態建構查詢時。 在此情況下，您也可以考慮使用 <xref:System.Data.Objects.ObjectQuery%601> 的查詢產生器方法，而不在執行階段建構 Entity SQL 查詢字串。  
  
-   當您想要將查詢定義為模型定義的一部分時。 資料模型僅支援 Entity SQL。 如需詳細資訊，請參閱[QueryView 項目 (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
-   使用 EntityClient 傳回唯讀實體資料，做為使用 <xref:System.Data.EntityClient.EntityDataReader> 的資料列集時。 如需詳細資訊，請參閱 < [Entity Framework 的 EntityClient 提供者](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。  
  
-   如果您非常熟悉 SQL 查詢語言，對您來說，Entity SQL 可能最易於使用。  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>搭配 EntityClient 提供者使用 Entity SQL  
 如果您想要搭配 EntityClient 提供者使用 Entity SQL，請參閱下列主題取得詳細資訊：  
  
 [Entity Framework 的 EntityClient 提供者](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [HOW TO：建置 EntityCollection 連接字串](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [HOW TO：執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [HOW TO：執行可傳回 RefType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [HOW TO：執行可傳回複雜類型的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [HOW TO：執行可傳回巢狀集合的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [HOW TO：使用 EntityCommand 執行參數化 Entity SQL 查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [HOW TO：使用 EntityCommand 執行參數化預存程序](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [HOW TO：執行多型查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [HOW TO：使用 Navigate 運算子巡覽關聯性](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>搭配物件查詢使用 Entity SQL  
 如果您想要搭配物件查詢使用 Entity SQL，請參閱下列主題取得詳細資訊：  
  
 [HOW TO：執行可傳回實體類型集合的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [HOW TO：執行參數化的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [HOW TO：使用導覽屬性導覽關聯性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [HOW TO：呼叫使用者定義函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [HOW TO：篩選資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [HOW TO：排序資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [HOW TO：群組資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [HOW TO：彙總資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [HOW TO：執行可傳回匿名類型集合的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [HOW TO：執行可傳回基本型別的集合的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [HOW TO：EntityCollection 中查詢相關的物件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [HOW TO：排序兩個查詢的聯集](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [HOW TO：逐頁查看查詢結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>本節內容  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
- [語言參考](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
