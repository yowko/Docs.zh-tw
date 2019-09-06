---
title: 具名類型建構函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: c7027614e5667acedb02d871a09df1ac9d799405
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250012"
---
# <a name="named-type-constructor-entity-sql"></a>具名類型建構函式 (Entity SQL)
用於建立概念模型名義型別 (例如實體類型或複雜類型) 的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>引數  
 `identifier`  
 為簡單或引號識別項的值。 如需詳細資訊，請參閱[識別碼](identifiers-entity-sql.md)  
  
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
  
1. [遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>另請參閱

- [建構類型](constructing-types-entity-sql.md)
- [Entity SQL 參考](entity-sql-reference.md)
