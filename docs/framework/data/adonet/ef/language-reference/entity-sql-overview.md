---
title: Entity SQL 概觀
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 8f40a34f361669d2b8d89b63b3187cae6bf705d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854492"
---
# <a name="entity-sql-overview"></a>Entity SQL 概觀
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]是一種類似 SQL 的語言，可讓您查詢 Entity Framework 中的概念模型。 概念模型會將資料表示為實體和關聯[!INCLUDE[esql](../../../../../../includes/esql-md.md)]性，並可讓您以熟悉使用 SQL 之物件的格式來查詢這些實體和關聯性。  
      
 此 Entity Framework 可與儲存體特定的資料提供者搭配使用[!INCLUDE[esql](../../../../../../includes/esql-md.md)] ，以將泛型轉譯成特定儲存體的查詢。 EntityClient 提供者會提供一個方式來針對實體模型執行 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 命令，並傳回豐富的資料型別，包括純量結果、結果集和物件圖形。 當您建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢的文字，其方式是將 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢字串指派給它的 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 屬性。 <xref:System.Data.EntityClient.EntityDataReader> 會公開針對 EDM 執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。 若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。  
  
 除了 EntityClient 提供者之外，Entity Framework 可讓您使用[!INCLUDE[esql](../../../../../../includes/esql-md.md)]針對概念模型執行查詢，並傳回資料做為實體類型實例的強型別 CLR 物件。 如需詳細資訊，請參閱[使用物件](../working-with-objects.md)。  
  
 本章節提供有關 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 的概念資訊。  
  
## <a name="in-this-section"></a>本節內容  
 [Entity SQL 與 Transact-SQL 的相異之處](how-entity-sql-differs-from-transact-sql.md)  
  
 [Entity SQL 快速參考](entity-sql-quick-reference.md)  
  
 [類型系統](type-system-entity-sql.md)  
  
 [型別定義](type-definitions-entity-sql.md)  
  
 [建構類型](constructing-types-entity-sql.md)  
  
 [查詢計劃快取](query-plan-caching-entity-sql.md)  
  
 [命名空間](namespaces-entity-sql.md)  
  
 [識別項](identifiers-entity-sql.md)  
  
 [參數](parameters-entity-sql.md)  
  
 [變數](variables-entity-sql.md)  
  
 [不支援的運算式](unsupported-expressions-entity-sql.md)  
  
 [常值](literals-entity-sql.md)  
  
 [Null 常值和型別推斷](null-literals-and-type-inference-entity-sql.md)  
  
 [輸入字元集](input-character-set-entity-sql.md)  
  
 [查詢運算式](query-expressions-entity-sql.md)  
  
 [函式](functions-entity-sql.md)  
  
 [運算子優先順序](operator-precedence-entity-sql.md)  
  
 [分頁](paging-entity-sql.md)  
  
 [比較語意](comparison-semantics-entity-sql.md)  
  
 [撰寫巢狀 Entity SQL 查詢](composing-nested-entity-sql-queries.md)  
  
 [可為 Null 的結構類型](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [Entity SQL 語言](entity-sql-language.md)
- [CSDL、SSDL 和 MSL 規格](csdl-ssdl-and-msl-specifications.md)
