---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: eae4387bcd5cbaf381ebf7169b6bc54d60328377
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309299"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
判斷運算式是否會產生所指定範圍內的值。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN 運算式具有相同的功能，做為 TRANSACT-SQL BETWEEN 運算式。  
  
## <a name="syntax"></a>語法  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 用來測試是否在 `begin_expression` 和 `end_expression` 所定義範圍中的任何有效運算式。 `expression` 必須是相同的類型`begin_expression`和`end_expression`。  
  
 `begin_expression`  
 任何有效的運算式。 `begin_expression` 必須是相同的類型`expression`和`end_expression`。 `begin_expression` 應小於`end_expression`，否則便會否定傳回值。  
  
 `end_expression`  
 任何有效的運算式。 `end_expression` 必須是相同的類型`expression`和`begin_expression`。  
  
 NOT  
 指定要否定 BETWEEN 的結果。  
  
 AND  
 做為一個預留位置，用來指出 `expression` 應該在 `begin_expression` 和 `end_expression` 所指示的範圍內。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果`expression`所指定的範圍之間`begin_expression`並`end_expression`; 否則`false`。 `null` 會傳回`expression`是`null`或者`begin_expression`或是`end_expression`是`null`。  
  
## <a name="remarks"></a>備註  
 若要指定排除範圍，請使用大於 (>) 和小於 (<) 運算子來取代 BETWEEN。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用 BETWEEN 運算子來判斷運算式是否會產生所指定範圍內的值。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
