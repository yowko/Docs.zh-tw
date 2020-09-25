---
title: OVERLAPS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 6902a44af343c37ccb26412738d9f96b28551814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204420"
---
# <a name="overlaps-entity-sql"></a>OVERLAPS (Entity SQL)

判斷兩個集合是否有共同項目。  
  
## <a name="syntax"></a>語法  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>引數  

 `expression`  
 任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。 所有運算式都必須具有與 `expression`相同的型別或是共同基底型別或衍生型別。  
  
## <a name="return-value"></a>傳回值  

 如果兩個集合有共同項目則為`true` ；否則為 `false`。  
  
## <a name="remarks"></a>備註  

 重迭提供功能相當於下列專案：  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 OVERLAPS 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。 如需設定運算子的優先順序資訊 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ，請參閱 [EXCEPT](except-entity-sql.md)。  
  
## <a name="example"></a>範例  

 下列 Entity SQL 查詢會使用 OVERLAPS 運算子來判斷兩個集合是否具有共通的值。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
