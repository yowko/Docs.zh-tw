---
title: "具名類型建構函式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ab743f3132dc15548735771b13967898b4c3f15f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="named-type-constructor-entity-sql"></a>具名類型建構函式 (Entity SQL)
用於建立概念模型名義型別 (例如實體類型或複雜類型) 的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>引數  
 `identifier`  
 為簡單或引號識別項的值。 如需詳細資訊，請參閱[識別項](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 型別的屬性，假設與它們出現在型別宣告中的順序相同。  
  
## <a name="return-value"></a>傳回值  
 具名複雜類型和實體類型的執行個體。  
  
## <a name="remarks"></a>備註  
 以下範例示範如何建構名義和複雜類型。  
  
 下面的運算式會建立 `Person` 型別的執行個體：  
  
 `Person("abc", 12)`  
  
 下面的運算式會建立複雜類型的執行個體：  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 下面的運算式會建立巢狀複雜類型的執行個體：  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 下面的運算式會建立具有巢狀複雜類型之實體的執行個體：  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 以下範例示範如何將複雜類型的屬性初始化為：`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用具名型別建構函式來建立概念模型型別的執行個體。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>請參閱  
 [建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
