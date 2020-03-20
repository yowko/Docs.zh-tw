---
title: FUNCTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: fd7f484733e7135d2d6c8094b6527d672a988088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150294"
---
# <a name="function-entity-sql"></a>FUNCTION (Entity SQL)
定義 Entity SQL 查詢命令範圍內的函式。  
  
## <a name="syntax"></a>語法  
  
```sql  
FUNCTION function-name  
( [ { parameter_name <type_definition>
        [ ,...n ]  
  ]  
) AS ( function_expression )
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )
                | REF ( data_type )
                | ROW ( row_expression )
        }
```  
  
## <a name="arguments"></a>引數  
 `function-name`  
 函數的名稱。  
  
 `parameter-name`  
 函式中的參數名稱。  
  
 `function_expression`  
 有效的 Entity SQL 運算式是函式。 函式中的命令可以在傳遞至函式的 `parameter_name` 參數上作用。  
  
 `data_type`  
 支援的型別名稱。  
  
 收藏 （`>` <type_definition ）  
 傳回支援的型別、資料列或參考等集合的運算式。  
  
 參考 **（**`data_type`**）**  
 傳回實體類型之參考的運算式。  
  
 行 **（**`row_expression`**）**  
 從一或多個值傳回匿名、結構式型別記錄的運算式。 如需詳細資訊，請參閱 [ROW](row-entity-sql.md)。  
  
## <a name="remarks"></a>備註  
 只要函式簽章是不一樣的，含相同名稱的多個函式即可宣告為內嵌。 如需詳細資訊，請參閱 [Function Overload Resolution](function-overload-resolution-entity-sql.md)。  
  
 內嵌函式必須先在 Entity SQL 命令中定義，才能在 Entity SQL 命令中呼叫。 不過，在定義呼叫的函式之前或之後，可在另一個內嵌函式中呼叫內嵌函式。 在下列範例中，在定義函式 B 之前，函式 A 呼叫函式 B：  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 如需詳細資訊，請參閱 [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))。  
  
 函式也可以在模型本身進行宣告。 在模型中宣告的函式，會與在命令中宣告為內嵌的函式一樣，以相同的方式執行。 有關詳細資訊，請參閱[使用者定義的函數](user-defined-functions-entity-sql.md)。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 命令定義函式 `Products` ，使用整數值篩選傳回的產品。  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a>範例  
 以下 Entity SQL 命令定義函式 `StringReturnsCollection` ，使用字串集合篩選傳回的連絡人。  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [Entity SQL 語言](entity-sql-language.md)
