---
title: Entity SQL 概觀
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 880b81f2b6d4c4b893d28c919490f88dfb2a42e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150372"
---
# <a name="entity-sql-overview"></a>Entity SQL 概觀
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]是一種類似于 SQL 的語言，使您能夠在實體框架中查詢概念模型。 概念模型將資料表示為實體和關係，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]並允許您以使用 SQL 的實體和關係所熟悉的格式查詢這些實體和關係。  

 實體框架與特定于存儲的資料提供程式合作，將泛型[!INCLUDE[esql](../../../../../../includes/esql-md.md)]轉換為特定于存儲的查詢。 EntityClient 提供者會提供一個方式來針對實體模型執行 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 命令，並傳回豐富的資料型別，包括純量結果、結果集和物件圖形。 當您建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢的文字，其方式是將 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢字串指派給它的 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 屬性。 <xref:System.Data.EntityClient.EntityDataReader> 會公開針對 EDM 執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。 若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。  
  
 除了 EntityClient 提供程式之外，實體框架還允許您使用[!INCLUDE[esql](../../../../../../includes/esql-md.md)]執行針對概念模型的查詢，並將資料作為實體類型的實例的強型別 CLR 物件返回資料。 有關詳細資訊，請參閱[使用物件](../working-with-objects.md)。  
  
 本章節提供有關 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 的概念資訊。  
  
## <a name="in-this-section"></a>本節內容  
 [Entity SQL 與 Transact-SQL 的相異之處](how-entity-sql-differs-from-transact-sql.md)  
  
 [Entity SQL 快速參考](entity-sql-quick-reference.md)  
  
 [型別系統](type-system-entity-sql.md)  
  
 [類型定義](type-definitions-entity-sql.md)  
  
 [建構類型](constructing-types-entity-sql.md)  
  
 [查詢計劃快取](query-plan-caching-entity-sql.md)  
  
 [命名空間](namespaces-entity-sql.md)  
  
 [識別碼](identifiers-entity-sql.md)  
  
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
- [CSDL、SSDL 和 MSL 規格](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
