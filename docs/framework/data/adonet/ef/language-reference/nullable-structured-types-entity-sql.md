---
title: 可為 Null 的結構類型 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6b949cebfa1b16f8e6fb5a133c61c5668d90b3bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762383"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="f977e-102">可為 Null 的結構類型 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f977e-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="f977e-103">結構化型別的 `null` 執行個體是不存在的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f977e-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="f977e-104">這與現有的執行個體 (所有的屬性都有 `null` 值) 不同。</span><span class="sxs-lookup"><span data-stu-id="f977e-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="f977e-105">本主題描述可為 Null 的結構化型別，其中包括哪些型別可為 Null，以及哪些程式碼模式會產生可為 Null 之結構化型別的 `null` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f977e-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="f977e-106">可為 Null 的結構化型別種類</span><span class="sxs-lookup"><span data-stu-id="f977e-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="f977e-107">可為 Null 的結構化型別有三種：</span><span class="sxs-lookup"><span data-stu-id="f977e-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="f977e-108">資料列型別。</span><span class="sxs-lookup"><span data-stu-id="f977e-108">Row types.</span></span>  
  
-   <span data-ttu-id="f977e-109">複雜類型。</span><span class="sxs-lookup"><span data-stu-id="f977e-109">Complex types.</span></span>  
  
-   <span data-ttu-id="f977e-110">實體類型。</span><span class="sxs-lookup"><span data-stu-id="f977e-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="f977e-111">產生結構化型別之 Null 執行個體的程式碼模式</span><span class="sxs-lookup"><span data-stu-id="f977e-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="f977e-112">下列案例會產生 `null` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="f977e-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="f977e-113">將 `null` 定形為結構化型別：</span><span class="sxs-lookup"><span data-stu-id="f977e-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="f977e-114">將基底型別向上轉型成衍生型別：</span><span class="sxs-lookup"><span data-stu-id="f977e-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="f977e-115">false 條件上的外部聯結 (Outer Join)：</span><span class="sxs-lookup"><span data-stu-id="f977e-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="f977e-116">--或</span><span class="sxs-lookup"><span data-stu-id="f977e-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="f977e-117">--或</span><span class="sxs-lookup"><span data-stu-id="f977e-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="f977e-118">為 `null` 參考取值：</span><span class="sxs-lookup"><span data-stu-id="f977e-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="f977e-119">從空的集合中取得 ANYELEMENT：</span><span class="sxs-lookup"><span data-stu-id="f977e-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="f977e-120">檢查是否有結構化型別的 `null` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="f977e-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f977e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f977e-121">See Also</span></span>  
 [<span data-ttu-id="f977e-122">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="f977e-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
