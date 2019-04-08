---
title: 具名類型建構函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 26fb2839f0cc7d645f6ce6daea2d27e35868b63c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168788"
---
# <a name="named-type-constructor-entity-sql"></a>具名類型建構函式 (Entity SQL)
用於建立概念模型名義型別 (例如實體類型或複雜類型) 的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>引數  
 `identifier`  
 為簡單或引號識別項的值。 如需詳細資訊，請參閱[識別碼](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
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
  
 下列範例示範如何初始化為 null 的複雜類型的屬性：`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>範例  
 以下 Entity SQL 查詢使用具名型別建構函式來建立概念模型型別的執行個體。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>另請參閱

- [建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
