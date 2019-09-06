---
title: OVERLAPS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: fef90beebf1c2723c767eaf5155542ad40d5fcb8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249727"
---
# <a name="overlaps-entity-sql"></a>OVERLAPS (Entity SQL)
判斷兩個集合是否有共同項目。  
  
## <a name="syntax"></a>語法  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。 所有運算式都必須具有與 `expression`相同的型別或是共同基底型別或衍生型別。  
  
## <a name="return-value"></a>傳回值  
 如果兩個集合有共同項目則為`true` ；否則為 `false`。  
  
## <a name="remarks"></a>備註  
 重迭提供的功能相當於下列內容：  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 OVERLAPS 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。 如需[!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子的優先順序資訊，請參閱[EXCEPT](except-entity-sql.md)。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 OVERLAPS 運算子來判斷兩個集合是否具有共通的值。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
