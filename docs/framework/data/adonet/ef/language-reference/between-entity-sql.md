---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251288"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
判斷運算式是否會產生所指定範圍內的值。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Between 運算式與 expression 之間的 transact-sql 具有相同的功能。  
  
## <a name="syntax"></a>語法  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 用來測試是否在 `begin_expression` 和 `end_expression` 所定義範圍中的任何有效運算式。 `expression` 必須與 `begin_expression` 和 `end_expression` 兩者型別相同。  
  
 `begin_expression`  
 任何有效的運算式。 `begin_expression` 必須與 `expression` 和 `end_expression` 兩者型別相同。 `begin_expression` 應小於 `end_expression`，否則便會否定傳回值。  
  
 `end_expression`  
 任何有效的運算式。 `end_expression` 必須與 `expression` 和 `begin_expression` 兩者型別相同。  
  
 NOT  
 指定要否定 BETWEEN 的結果。  
  
 AND  
 做為一個預留位置，用來指出 `expression` 應該在 `begin_expression` 和 `end_expression` 所指示的範圍內。  
  
## <a name="return-value"></a>傳回值  
 如果 `true` 是在 `expression` 和 `begin_expression` 所指定的範圍內則為 `end_expression`；否則為 `false`。 如果 `null` 為 `expression`，或者 `null` 或 `begin_expression` 為 `end_expression`，便會傳回 `null`。  
  
## <a name="remarks"></a>備註  
 若要指定獨佔範圍，請使用大於（>）和小於（<）運算子，而不是介於之間。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用 BETWEEN 運算子來判斷運算式是否會產生所指定範圍內的值。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
