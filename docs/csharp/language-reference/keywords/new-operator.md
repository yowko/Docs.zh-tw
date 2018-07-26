---
title: new 運算子 (C# 參考)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243943"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="3de5e-102">new 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3de5e-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="3de5e-103">用以建立物件及叫用建構函式。</span><span class="sxs-lookup"><span data-stu-id="3de5e-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="3de5e-104">例如: </span><span class="sxs-lookup"><span data-stu-id="3de5e-104">For example:</span></span>  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="3de5e-105">它也用來建立匿名型別的執行個體︰</span><span class="sxs-lookup"><span data-stu-id="3de5e-105">It is also used to create instances of anonymous types:</span></span>  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 <span data-ttu-id="3de5e-106">`new` 運算子也可以用來叫用實值型別的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="3de5e-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="3de5e-107">例如: </span><span class="sxs-lookup"><span data-stu-id="3de5e-107">For example:</span></span>  
  
```csharp
int i = new int();  
```  
  
 <span data-ttu-id="3de5e-108">在前一個陳述式中，`i` 會初始化為 `0`，這是 `int` 型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="3de5e-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="3de5e-109">此陳述式與下例效果相同：</span><span class="sxs-lookup"><span data-stu-id="3de5e-109">The statement has the same effect as the following:</span></span>  
  
```csharp
int i = 0;  
```  
  
 <span data-ttu-id="3de5e-110">如需預設值的完整清單，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。</span><span class="sxs-lookup"><span data-stu-id="3de5e-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="3de5e-111">請記住，為 [struct](../../../csharp/language-reference/keywords/struct.md) 宣告預設建構函式是錯誤，因為每一個實值型別都有隱含的公用預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="3de5e-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="3de5e-112">在結構型別上宣告參數化建構函式以設定其初始值是可能的，但只有需要預設值以外的值時才為必要。</span><span class="sxs-lookup"><span data-stu-id="3de5e-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="3de5e-113">實質型別物件 (如結構) 與參考型別物件 (如類別) 皆會自動終結，但實質型別物件會在其包含的內容終結時終結，而參考型別物件則會在以其為目標的上一個參考移除時，在非指定時間由記憶體回收行程終結。</span><span class="sxs-lookup"><span data-stu-id="3de5e-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="3de5e-114">對於包含檔案處理常式或網路連線等資源的類型而言，最好採用確定性清除來確保其包含的資源盡早釋出。</span><span class="sxs-lookup"><span data-stu-id="3de5e-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="3de5e-115">如需詳細資訊，請參閱[使用陳述式](../../../csharp/language-reference/keywords/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3de5e-115">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="3de5e-116">無法多載 `new` 運算子。</span><span class="sxs-lookup"><span data-stu-id="3de5e-116">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="3de5e-117">如果 `new` 運算子無法配置記憶體，則會擲回例外狀況 <xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="3de5e-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3de5e-118">範例</span><span class="sxs-lookup"><span data-stu-id="3de5e-118">Example</span></span>  
 <span data-ttu-id="3de5e-119">下例使用 `new` 運算子建立並初始化 `struct` 物件和類別物件，然後為物件指派值。</span><span class="sxs-lookup"><span data-stu-id="3de5e-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="3de5e-120">顯示預設值和指派的值。</span><span class="sxs-lookup"><span data-stu-id="3de5e-120">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="3de5e-121">請注意，範例中的字串預設值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="3de5e-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="3de5e-122">因此，不會顯示。</span><span class="sxs-lookup"><span data-stu-id="3de5e-122">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3de5e-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3de5e-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3de5e-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="3de5e-124">See Also</span></span>  
 [<span data-ttu-id="3de5e-125">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3de5e-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3de5e-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3de5e-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3de5e-127">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="3de5e-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3de5e-128">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="3de5e-128">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="3de5e-129">new</span><span class="sxs-lookup"><span data-stu-id="3de5e-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="3de5e-130">匿名類型</span><span class="sxs-lookup"><span data-stu-id="3de5e-130">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
