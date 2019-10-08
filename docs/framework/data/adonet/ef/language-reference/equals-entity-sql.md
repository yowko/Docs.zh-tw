---
title: = (等號) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 5cdfd35450514a9699a39cf78f64c0fa6b7d5f39
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833844"
---
# <a name="-equals-entity-sql"></a>= (等號) (Entity SQL)
比較兩個運算式是否相等。  
  
## <a name="syntax"></a>語法  
  
```sql  
expression = expression  
-- or   
expression == expression  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何有效的運算式。 兩個運算式都必須有可隱含轉換的資料型別。  
  
## <a name="result-types"></a>結果型別  
 如果左運算式等於右運算式則為`true` ；否則為 `false`。  
  
## <a name="remarks"></a>備註  
 == 運算子就相當於 =。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用 = 比較運算子來比較兩個運算式是否相等。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 依照 [How 中的程式進行：執行可傳回 StructuralType 結果 @ no__t-0 的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
