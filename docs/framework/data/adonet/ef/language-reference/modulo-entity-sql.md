---
title: (模數) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 25bd34db3a627fa708e1ab9a3f0e237426487bcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175703"
---
# <a name="modulo-entity-sql"></a>(模數) (Entity SQL)

傳回某個運算式除以另一個運算式的餘數。  
  
## <a name="syntax"></a>語法  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a>引數  

 `dividend`  
 要當做被除數的數值運算式。 `dividend` 是任何一個數值資料型別的任何有效運算式。  
  
 `divisor`  
 要當做除數的數值運算式。 `divisor` 是任何一個數值資料型別的任何有效運算式。  
  
## <a name="result-types"></a>結果類型  

 Edm.Int32  
  
## <a name="example"></a>範例  

 下列 Entity SQL 查詢會使用 % 算術運算子來傳回某個運算式除以另一個運算式的餘數。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
