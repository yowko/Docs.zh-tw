---
title: '-  (減去)  (Entity SQL) '
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 17841f336ed186dcbc50b84254048546b15297e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181033"
---
# <a name="--subtract-entity-sql"></a>- (減號) (Entity SQL)

兩個數字相減。  
  
## <a name="syntax"></a>語法  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a>引數  

 `expression`  
 任何一個數值資料型別的任何有效運算式。  
  
## <a name="result-types"></a>結果類型  

 從兩個引數的隱含型別提升產生的資料型別。 如需隱含類型升級的詳細資訊，請參閱 [類型系統](type-system-entity-sql.md)。  
  
## <a name="example"></a>範例  

 下列 Entity SQL 查詢會使用 - 算術運算子讓兩個數字相減。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
