---
title: '!= (不等於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: c2ccadaa5801cac9c10241108f02ade223a8697f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249843"
---
# <a name="-not-equal-to-entity-sql"></a>!= (不等於) (Entity SQL)
比較兩個運算式來判斷左運算式是否不等於右運算式。 != (不等於) 運算子的功能相當於 <> 運算子。  
  
## <a name="syntax"></a>語法  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何有效的運算式。 兩個運算式都必須有可隱含轉換的資料型別。  
  
## <a name="result-types"></a>結果型別  
 如果左運算式不等於右運算式，則為`true` ，否則為 `false`。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢使用 != 運算子來比較兩個運算式，以判斷左運算式是否不等於右運算式。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
