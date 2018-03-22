---
title: ANYELEMENT (Entity SQL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 6e74fbac9c2c57c653f55f76bf165d7eaebd9cee
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
從多重值集合中擷取元素。  
  
## <a name="syntax"></a>語法  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 傳回可從中擷取元素之集合的任何有效查詢運算式。  
  
## <a name="return-value"></a>傳回值  
 如果集合具有多個元素，就是集合中的單一元素或任意元素。如果集合是空的，則傳回 `null`。 如果`collection`是集合型別的`Collection<T>`，然後`ANYELEMENT(collection)`是有效的運算式可產生執行個體的型別`T`。  
  
## <a name="remarks"></a>備註  
 ANYELEMENT 會從多重值集合中擷取任意元素。 例如，下列範例會嘗試從 `Customers`集合中擷取單一元素。  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>範例  
 下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢會使用 ANYELEMENT 運算子，從多重值集合中擷取元素。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [可為 Null 的結構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
