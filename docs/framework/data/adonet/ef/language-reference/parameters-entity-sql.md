---
title: 參數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249592"
---
# <a name="parameters-entity-sql"></a>參數 (Entity SQL)
參數是定義在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 外部的變數，通常是透過主應用程式語言使用的繫結 API 來定義。 每一個參數都有一個名稱和型別， 參數名稱定義于查詢運算式中, 並以 at (@) 符號做為前置詞。 這樣可讓它們避免與屬性名稱或查詢內定義的其他名稱混淆。  
  
 主應用程式語言的繫結 API 會提供用來繫結參數的 API。  
  
## <a name="example"></a>範例  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [Entity SQL 概觀](entity-sql-overview.md)
