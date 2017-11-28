---
title: "new 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3c2b484b9872a54ce42520de77a723b9edb441a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="b274e-102">new 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b274e-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="b274e-103">用以建立物件及叫用建構函式。</span><span class="sxs-lookup"><span data-stu-id="b274e-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="b274e-104">例如：</span><span class="sxs-lookup"><span data-stu-id="b274e-104">For example:</span></span>  
  
```  
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="b274e-105">它也用來建立匿名型別的執行個體︰</span><span class="sxs-lookup"><span data-stu-id="b274e-105">It is also used to create instances of anonymous types:</span></span>  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 <span data-ttu-id="b274e-106">`new` 運算子也可以用來叫用實值型別的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="b274e-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="b274e-107">例如：</span><span class="sxs-lookup"><span data-stu-id="b274e-107">For example:</span></span>  
  
```  
int i = new int();  
```  
  
 <span data-ttu-id="b274e-108">在前一個陳述式中，`i` 會初始化為 `0`，這是 `int` 型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="b274e-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="b274e-109">此陳述式與下例效果相同：</span><span class="sxs-lookup"><span data-stu-id="b274e-109">The statement has the same effect as the following:</span></span>  
  
```  
int i = 0;  
```  
  
 <span data-ttu-id="b274e-110">如需預設值的完整清單，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。</span><span class="sxs-lookup"><span data-stu-id="b274e-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="b274e-111">請記住，為 [struct](../../../csharp/language-reference/keywords/struct.md) 宣告預設建構函式是錯誤，因為每一個實值型別都有隱含的公用預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="b274e-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="b274e-112">在結構型別上宣告參數化建構函式以設定其初始值是可能的，但只有需要預設值以外的值時才為必要。</span><span class="sxs-lookup"><span data-stu-id="b274e-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="b274e-113">結構等實值型別物件是建立在堆疊上，而類別等參考型別物件則是建立在堆積上。</span><span class="sxs-lookup"><span data-stu-id="b274e-113">Value-type objects such as structs are created on the stack, while reference-type objects such as classes are created on the heap.</span></span> <span data-ttu-id="b274e-114">這兩種物件型別都會自動終結，但實值型別物件是在超出範圍時終結，而參考型別物件則是在移除其最後一個參考後的未指定時間終結。</span><span class="sxs-lookup"><span data-stu-id="b274e-114">Both types of objects are destroyed automatically, but objects based on value types are destroyed when they go out of scope, whereas objects based on reference types are destroyed at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="b274e-115">對於使用大量記憶體、檔案控制代碼或網路連線等固定資源的參考類型而言，有時候非常需要採用具決定性的最終處理，以確保儘速終結物件。</span><span class="sxs-lookup"><span data-stu-id="b274e-115">For reference types that consume fixed resources such as large amounts of memory, file handles, or network connections, it is sometimes desirable to employ deterministic finalization to ensure that the object is destroyed as soon as possible.</span></span> <span data-ttu-id="b274e-116">如需詳細資訊，請參閱[使用陳述式](../../../csharp/language-reference/keywords/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b274e-116">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="b274e-117">`new` 運算子無法多載。</span><span class="sxs-lookup"><span data-stu-id="b274e-117">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="b274e-118">如果 `new` 運算子無法配置記憶體，則會擲回例外狀況 <xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="b274e-118">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b274e-119">範例</span><span class="sxs-lookup"><span data-stu-id="b274e-119">Example</span></span>  
 <span data-ttu-id="b274e-120">下例使用 `new` 運算子建立並初始化 `struct` 物件和類別物件，然後為物件指派值。</span><span class="sxs-lookup"><span data-stu-id="b274e-120">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="b274e-121">顯示預設值和指派的值。</span><span class="sxs-lookup"><span data-stu-id="b274e-121">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="b274e-122">請注意，範例中的字串預設值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="b274e-122">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="b274e-123">因此，不會顯示。</span><span class="sxs-lookup"><span data-stu-id="b274e-123">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b274e-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b274e-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b274e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b274e-125">See Also</span></span>  
 [<span data-ttu-id="b274e-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b274e-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b274e-127">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b274e-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b274e-128">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b274e-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b274e-129">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="b274e-129">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="b274e-130">new</span><span class="sxs-lookup"><span data-stu-id="b274e-130">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="b274e-131">匿名類型</span><span class="sxs-lookup"><span data-stu-id="b274e-131">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
