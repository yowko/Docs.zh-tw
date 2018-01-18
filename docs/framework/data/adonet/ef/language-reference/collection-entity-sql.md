---
title: COLLECTION (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f77989d367509c9d3526bfbdf8ebd50e7d9fc524
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="collection-entity-sql"></a>COLLECTION (Entity SQL)
COLLECTION 關鍵字只用於內嵌函式的定義。 集合函式是處理值的集合並產生純量輸出的函式。  
  
## <a name="syntax"></a>語法  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>引數  
 `type_definition`  
 傳回支援的型別、資料列或參考等集合的運算式。  
  
## <a name="remarks"></a>備註  
 如需 COLLECTION 關鍵字的詳細資訊，請參閱 [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 COLLECTION 關鍵字將十進位的集合宣告為內嵌查詢函式的引數。  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
