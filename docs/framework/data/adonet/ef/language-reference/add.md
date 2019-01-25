---
title: + （新增）
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: 1c525a1cd56d1d8b7ed0dad3a7cec686cb6b1ab3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580651"
---
# <a name="-add"></a>+ (加號)
將兩個數字相加。  
  
## <a name="syntax"></a>語法  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何一個數值資料型別的任何有效運算式。  
  
## <a name="result-types"></a>結果型別  
 從兩個引數的隱含型別提升產生的資料型別。 如需有關隱含型別提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。  
  
## <a name="remarks"></a>備註  
 若為 EDM.String 型別，加法就會串連。  
  
## <a name="example"></a>範例  
 下列 Entity SQL 查詢會使用 + 算術運算子讓兩個數字相加。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a>另請參閱
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [概念模型類型 (CSDL)](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
