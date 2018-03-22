---
title: (模數) (Entity SQL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e204612904aa55b4a0ae9aa65f2bbfd644bbc396
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="modulo-entity-sql"></a>(模數) (Entity SQL)
傳回某個運算式除以另一個運算式的餘數。  
  
## <a name="syntax"></a>語法  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>引數  
 `dividend`  
 要當做被除數的數值運算式。 `dividend` 是任何一個數值資料型別的任何有效運算式。  
  
 `divisor`  
 要當做除數的數值運算式。 `divisor` 是任何一個數值資料型別的任何有效運算式。  
  
## <a name="result-types"></a>結果型別  
 Edm.Int32  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 % 算術運算子來傳回某個運算式除以另一個運算式的餘數。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
