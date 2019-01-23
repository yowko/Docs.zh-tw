---
title: 。 (成員存取) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: e2874e5bff8d8c34f700a81bf52c6729df49aca5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626659"
---
# <a name="-member-access-entity-sql"></a>。 (成員存取) (Entity SQL)
點運算子 （.） 是[!INCLUDE[esql](../../../../../../includes/esql-md.md)]成員存取運算子。 使用成員存取運算子可產生結構化概念模型型別執行個體之屬性或欄位的值。  
  
## <a name="syntax"></a>語法  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 結構化概念模型型別的執行個體。  
  
 `identifier`  
 屬於物件執行個體的屬性或欄位。  
  
## <a name="remarks"></a>備註  
 點 (.) 運算子可以用來從記錄擷取欄位，就像是擷取複雜或實體類型的屬性。 舉例來講，假設 Name 型別的 n 是 Person 型別的成員，且 p 是 Person 型別的執行個體，則 p.n 便是產生 Name 型別值的合法成員存取運算式。  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>另請參閱
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
