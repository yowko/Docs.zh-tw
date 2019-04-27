---
title: FUNCTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: efab5f1abbc5e0c22e404c37dc80dd5aafa09ce1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879602"
---
# <a name="function-entity-sql"></a>FUNCTION (Entity SQL)
定義 Entity SQL 查詢命令範圍內的函式。  
  
## <a name="syntax"></a>語法  
  
```  
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
 函式的名稱。  
  
 `parameter-name`  
 函式中的參數名稱。  
  
 `function_expression`  
 有效的 Entity SQL 運算式是函式。 函式中的命令可以在傳遞至函式的 `parameter_name` 參數上作用。  
  
 `data_type`  
 支援的型別名稱。  
  
 集合 (< type_definition`>` )  
 傳回支援的型別、資料列或參考等集合的運算式。  
  
 REF **(**`data_type`**)**  
 傳回實體類型之參考的運算式。  
  
 ROW **(**`row_expression`**)**  
 從一或多個值傳回匿名、結構式型別記錄的運算式。 如需詳細資訊，請參閱 [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)。  
  
## <a name="remarks"></a>備註  
 只要函式簽章是不一樣的，含相同名稱的多個函式即可宣告為內嵌。 如需詳細資訊，請參閱 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)。  
  
 內嵌函式必須先在 Entity SQL 命令中定義，才能在 Entity SQL 命令中呼叫。 不過，在定義呼叫的函式之前或之後，可在另一個內嵌函式中呼叫內嵌函式。 在下列範例中，在定義函式 B 之前，函式 A 呼叫函式 B：  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 如需詳細資訊，請參閱[如何：呼叫使用者定義函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))。  
  
 函式也可以在模型本身進行宣告。 在模型中宣告的函式，會與在命令中宣告為內嵌的函式一樣，以相同的方式執行。 如需詳細資訊，請參閱 <<c0> [ 使用者定義函式](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)。  
  
## <a name="example"></a>範例  
 以下 Entity SQL 命令定義函式 `Products` ，使用整數值篩選傳回的產品。  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>範例  
 以下 Entity SQL 命令定義函式 `StringReturnsCollection` ，使用字串集合篩選傳回的連絡人。  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL 語言](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
