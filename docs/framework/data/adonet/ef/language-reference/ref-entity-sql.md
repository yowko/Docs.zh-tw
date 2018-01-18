---
title: REF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 226a14daa706f6cf0481b752fa03dc95db3eff81
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
傳回實體執行個體的參考。  
  
## <a name="syntax"></a>語法  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 可產生實體類型之執行個體的任何有效運算式。  
  
## <a name="return-value"></a>傳回值  
 指定之實體執行個體的參考。  
  
## <a name="remarks"></a>備註  
 實體參考由實體索引鍵和實體集名稱所組成。 因為不同實體集可視相同實體類型而定，特定實體索引鍵可出現於多個實體集， 但實體參考一定是唯一的。 如果輸入運算式表示持續性實體，會傳回這個實體的參考。 如果輸入運算式不是持續性實體，會傳回 null 參考。  
  
 如果屬性引出運算子 (.) 是用於存取實體的屬性，則會為參考自動取值 (Dereference)。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 REF 運算子，傳回輸入實體引數的參考。 相同查詢會為參考取值，因為我們使用屬性引出運算子 (.) 存取 Product 實體的屬性。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  請依照下列中的程序[如何： 執行查詢，傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2.  將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>請參閱  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [型別定義](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
