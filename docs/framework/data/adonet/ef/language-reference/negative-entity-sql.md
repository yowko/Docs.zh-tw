---
title: '-  (負)  (Entity SQL) '
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 71749dab073fade854c2a494841e3f6b408ebd1d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204407"
---
# <a name="--negative-entity-sql"></a>- (負號) (Entity SQL)

傳回數值運算式的負值。  
  
## <a name="syntax"></a>語法  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a>引數  

 `expression`  
 任何一個數值資料型別的任何有效運算式。  
  
## <a name="result-types"></a>結果類型  

 `expression` 的資料類型。  
  
## <a name="remarks"></a>備註  

 如果 `expression` 是不帶正負號型別，結果型別就是與 `expression`型別最密切相關的帶正負號型別。 例如，如果 `expression` 的型別為 Byte，就會傳回 Int16 型別的值。  
  
## <a name="example"></a>範例  

 下列 Entity SQL 查詢會使用 - 算術運算子來傳回數值運算式的負值。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
