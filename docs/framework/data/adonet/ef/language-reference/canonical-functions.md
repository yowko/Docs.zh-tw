---
title: 標準函式
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: f8ca9e2027e82db89e91287fda02d2014d53f325
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854507"
---
# <a name="canonical-functions"></a>標準函式
本節討論所有資料提供者都支援，而且可由所有查詢技術使用的標準函式。 標準函式無法由提供者擴允。  
  
 這些標準函式將會轉譯成提供者的對應資料來源功能， 這樣一來就能以跨資料來源的通用形式表示函式引動過程。  
  
 由於這些標準函式與資料來源無關，所以標準函式的引數和傳回型別是以概念模型中的型別定義。 不過，某些資料來源可能無法支援概念模型中的所有型別。  
  
 在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢中使用標準函式時，會在資料來源中呼叫適當的函式。  
  
 所有標準函式都必須明確指定 null 輸入行為和錯誤條件。 存放區提供者應符合該行為，但 Entity Framework 不會強制執行此行為。  
  
 針對 LINQ 案例，針對 Entity Framework 的查詢牽涉到將 CLR 方法對應到基礎資料來源中的方法。 CLR 方法會對應到標準函式，這樣一來便會正確對應一組特定的方法，而不用顧慮資料來源為何。  
  
## <a name="canonical-functions-namespace"></a>標準函式命名空間  
 標準函式的命名空間為 <xref:System.Data.Metadata.Edm>。 <xref:System.Data.Metadata.Edm> 命名空間會自動包含在所有查詢中。 但是，如果匯入了另一個命名空間，包含與標準函式同名的函式 (在 <xref:System.Data.Metadata.Edm> 命名空間中)，您就必須指定命名空間。  
  
## <a name="in-this-section"></a>本節內容  
 [彙總標準函式](aggregate-canonical-functions.md)  
 討論彙總 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [數學標準函式](math-canonical-functions.md)  
 討論數學 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [字串標準函式](string-canonical-functions.md)  
 討論字串 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [日期和時間標準函式](date-and-time-canonical-functions.md)  
 討論日期和時間 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [位元標準函式](bitwise-canonical-functions.md)  
 討論位元運算 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [空間函式](spatial-functions.md)  
 討論空間 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
 [其他標準函式](other-canonical-functions.md)  
 討論未分類為位元運算、日期/時間、字串、數學或彙總的函式。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
- [Entity SQL 參考](entity-sql-reference.md)
- [概念模型標準與 SQL Server 函式的對應](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [使用者定義函式](user-defined-functions-entity-sql.md)
