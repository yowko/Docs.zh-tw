---
title: CAST (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 97971668430dd7721b15a4ac60e422fe06f0ed1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cast-entity-sql"></a>CAST (Entity SQL)
將一種資料類型的運算式轉換成另一種。  
  
## <a name="syntax"></a>語法  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 可以轉換為 `data_type`的任何有效運算式。  
  
 `data_type`  
 目標系統提供的資料型別。 它必須是基本 (純量) 型別。 使用的 `data_type` 視查詢空間而定。 如果查詢是以 <xref:System.Data.EntityClient.EntityCommand>執行的，資料型別會是在概念模型中定義的型別。 如需詳細資訊，請參閱 [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)。 如果查詢是以 <xref:System.Data.Objects.ObjectQuery%601>執行的，則資料型別為 Common Language Runtime (CLR) 型別。  
  
## <a name="return-value"></a>傳回值  
 傳回 `data_type`的相同值。  
  
## <a name="remarks"></a>備註  
 轉型運算式的語意很類似 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT 運算式。 轉型運算式是用來將某個型別的值轉換成另一個型別的值。  
  
```  
CAST( e as T )  
```  
  
 如果 e 為 S 型別，且 S 可轉換成 T，則上述運算式便是有效的轉型運算式。 T 必須是基本 (純量) 型別。  
  
 轉型為 `Edm.Decimal`時可選擇性提供有效位數和小數位數 Facet 的值。 如果沒有明確提供，則有效位數和小數位數的預設值將分別為 18 和 0。 更明確地講，下列多載支援 `Decimal`：  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 使用轉型運算式會視為明確轉換。 而明確轉換可能會截斷資料或遺失有效位數。  
  
> [!NOTE]
>  只有在基本型別和列舉成員型別上能支援 CAST。  
  
## <a name="example"></a>範例  
 下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 CAST 運算子將某個資料型別的運算式轉型為另一個資料型別。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  請依照下列中的程序[如何： 執行查詢，傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2.  將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
