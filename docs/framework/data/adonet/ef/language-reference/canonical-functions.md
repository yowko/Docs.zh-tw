---
title: 標準函式
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: fed6e45056e318ec0bf34951097304ef3c98f629
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="canonical-functions"></a>標準函式
本節討論所有資料提供者都支援，而且可由所有查詢技術使用的標準函式。 標準函式無法由提供者擴允。  
  
 這些標準函式將會轉譯成提供者的對應資料來源功能， 這樣一來就能以跨資料來源的通用形式表示函式引動過程。  
  
 由於這些標準函式與資料來源無關，所以標準函式的引數和傳回型別是以概念模型中的型別定義。 不過，某些資料來源可能無法支援概念模型中的所有型別。  
  
 在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢中使用標準函式時，會在資料來源中呼叫適當的函式。  
  
 所有標準函式都必須明確指定 null 輸入行為和錯誤條件。 存放區提供者應遵守該行為，但 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 並不強制執行此行為。  
  
 LINQ 案例而言，對查詢[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]將 CLR 方法對應至基礎資料來源中的方法。 CLR 方法會對應到標準函式，這樣一來便會正確對應一組特定的方法，而不用顧慮資料來源為何。  
  
## <a name="canonical-functions-namespace"></a>標準函式命名空間  
 標準函式的命名空間為 <xref:System.Data.Metadata.Edm>。 <xref:System.Data.Metadata.Edm> 命名空間會自動包含在所有查詢中。 但是，如果匯入了另一個命名空間，包含與標準函式同名的函式 (在 <xref:System.Data.Metadata.Edm> 命名空間中)，您就必須指定命名空間。  
  
## <a name="in-this-section"></a>本節內容  
 [彙總標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 討論彙總 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [數學標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 討論數學 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [字串標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 討論字串 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [日期和時間標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 討論日期和時間 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [位元標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 討論位元運算 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [空間函式](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 討論空間 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [其他標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 討論未分類為位元運算、日期/時間、字串、數學或彙總的函式。  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [概念模型標準與 SQL Server 函式的對應](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [使用者定義函式](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
