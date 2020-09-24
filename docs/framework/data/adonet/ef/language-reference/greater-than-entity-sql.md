---
title: '>  (大於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 52a9f9f645aa51402ceb8cb0a40d2040d1c0802c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147940"
---
# <a name="-greater-than-entity-sql"></a>> (大於)  (Entity SQL) 

比較兩個運算式來判斷左運算式的值是否大於右運算式。  
  
## <a name="syntax"></a>語法  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a>引數  

 `expression`  
 任何有效的運算式。 這兩個運算式的類型，都必須是可以隱含轉換的資料類型。  
  
## <a name="result-types"></a>結果類型  

 如果左運算式的值大於右運算式則為`true` ；否則為 `false`。  
  
## <a name="example"></a>範例  

 下列 Entity SQL 查詢使用 > 比較運算子來比較兩個運算式，以判斷左運算式的值是否大於右運算式。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
