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
# <a name="function-entity-sql"></a><span data-ttu-id="56ca9-102">FUNCTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="56ca9-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="56ca9-103">定義 Entity SQL 查詢命令範圍內的函式。</span><span class="sxs-lookup"><span data-stu-id="56ca9-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ca9-104">語法</span><span class="sxs-lookup"><span data-stu-id="56ca9-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="56ca9-105">引數</span><span class="sxs-lookup"><span data-stu-id="56ca9-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="56ca9-106">函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="56ca9-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="56ca9-107">函式中的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="56ca9-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="56ca9-108">有效的 Entity SQL 運算式是函式。</span><span class="sxs-lookup"><span data-stu-id="56ca9-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="56ca9-109">函式中的命令可以在傳遞至函式的 `parameter_name` 參數上作用。</span><span class="sxs-lookup"><span data-stu-id="56ca9-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="56ca9-110">支援的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="56ca9-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="56ca9-111">集合 (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="56ca9-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="56ca9-112">傳回支援的型別、資料列或參考等集合的運算式。</span><span class="sxs-lookup"><span data-stu-id="56ca9-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="56ca9-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="56ca9-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="56ca9-114">傳回實體類型之參考的運算式。</span><span class="sxs-lookup"><span data-stu-id="56ca9-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="56ca9-115">ROW **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="56ca9-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="56ca9-116">從一或多個值傳回匿名、結構式型別記錄的運算式。</span><span class="sxs-lookup"><span data-stu-id="56ca9-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="56ca9-117">如需詳細資訊，請參閱 [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="56ca9-117">For more information, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56ca9-118">備註</span><span class="sxs-lookup"><span data-stu-id="56ca9-118">Remarks</span></span>  
 <span data-ttu-id="56ca9-119">只要函式簽章是不一樣的，含相同名稱的多個函式即可宣告為內嵌。</span><span class="sxs-lookup"><span data-stu-id="56ca9-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="56ca9-120">如需詳細資訊，請參閱 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="56ca9-120">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="56ca9-121">內嵌函式必須先在 Entity SQL 命令中定義，才能在 Entity SQL 命令中呼叫。</span><span class="sxs-lookup"><span data-stu-id="56ca9-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="56ca9-122">不過，在定義呼叫的函式之前或之後，可在另一個內嵌函式中呼叫內嵌函式。</span><span class="sxs-lookup"><span data-stu-id="56ca9-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="56ca9-123">在下列範例中，在定義函式 B 之前，函式 A 呼叫函式 B：</span><span class="sxs-lookup"><span data-stu-id="56ca9-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="56ca9-124">如需詳細資訊，請參閱[如何：呼叫使用者定義函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="56ca9-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="56ca9-125">函式也可以在模型本身進行宣告。</span><span class="sxs-lookup"><span data-stu-id="56ca9-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="56ca9-126">在模型中宣告的函式，會與在命令中宣告為內嵌的函式一樣，以相同的方式執行。</span><span class="sxs-lookup"><span data-stu-id="56ca9-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="56ca9-127">如需詳細資訊，請參閱 <<c0> [ 使用者定義函式](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="56ca9-127">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ca9-128">範例</span><span class="sxs-lookup"><span data-stu-id="56ca9-128">Example</span></span>  
 <span data-ttu-id="56ca9-129">以下 Entity SQL 命令定義函式 `Products` ，使用整數值篩選傳回的產品。</span><span class="sxs-lookup"><span data-stu-id="56ca9-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="56ca9-130">範例</span><span class="sxs-lookup"><span data-stu-id="56ca9-130">Example</span></span>  
 <span data-ttu-id="56ca9-131">以下 Entity SQL 命令定義函式 `StringReturnsCollection` ，使用字串集合篩選傳回的連絡人。</span><span class="sxs-lookup"><span data-stu-id="56ca9-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="56ca9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56ca9-132">See also</span></span>

- [<span data-ttu-id="56ca9-133">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="56ca9-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="56ca9-134">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="56ca9-134">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
