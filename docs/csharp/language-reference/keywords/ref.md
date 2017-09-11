---
title: "ref (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: fe05a902dd053dfe788041842d59d7189a3fc9e4
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="ref-c-reference"></a><span data-ttu-id="ea9c7-102">ref (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ea9c7-102">ref (C# Reference)</span></span>
<span data-ttu-id="ea9c7-103">`ref` 關鍵字會導致引數由參考加以傳遞，而非透過值。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-103">The `ref` keyword causes an argument to be passed by reference, not by value.</span></span> <span data-ttu-id="ea9c7-104">由參考傳遞的效果，是呼叫方法中參數的任何變更，都會反映在呼叫方法中。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-104">The effect of passing by reference is that any change to the parameter in the called method is reflected in the calling method.</span></span> <span data-ttu-id="ea9c7-105">例如，如果呼叫端傳遞了區域變數運算式或陣列元素存取運算式，且被呼叫的方法取代了 ref 參數所參考的物件，則呼叫端的區域變數或陣列元素現在會參考新的物件。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-105">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refer to the new object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea9c7-106">請勿將參考傳遞的概念與參考類型的概念相混淆。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-106">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="ea9c7-107">兩個概念並不相同。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-107">The two concepts are not the same.</span></span> <span data-ttu-id="ea9c7-108">方法參數可以由 `ref` 修改，而不論其是否為實值類型或參考類型。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-108">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="ea9c7-109">當實值類型由參考傳遞時，沒有 boxing。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-109">There is no boxing of a value type when it is passed by reference.</span></span>  
  
 <span data-ttu-id="ea9c7-110">若要使用 `ref` 參數，方法定義和呼叫方法都必須明確使用 `ref` 關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-110">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  
  
 <span data-ttu-id="ea9c7-111">[!code-cs[csrefKeywordsMethodParams#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ea9c7-111">[!code-cs[csrefKeywordsMethodParams#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_1.cs)]</span></span>  
  
 <span data-ttu-id="ea9c7-112">傳遞至 `ref` 參數的引數，在傳遞之前必須先初始化。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-112">An argument that is passed to a `ref` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="ea9c7-113">這點與 `out` 參數不同，其引數不需要在傳遞之前先明確初始化。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-113">This differs from `out` parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span> <span data-ttu-id="ea9c7-114">如需詳細資訊，請參閱 [out](../../../csharp/language-reference/keywords/out.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-114">For more information, see [out](../../../csharp/language-reference/keywords/out.md).</span></span>  
  
 <span data-ttu-id="ea9c7-115">類別的成員不能擁有僅在 `ref` 和 `out` 方面不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-115">Members of a class can't have signatures that differ only by `ref` and `out`.</span></span> <span data-ttu-id="ea9c7-116">如果類型的兩個成員之間唯一的區別在於其中一個具有 `ref` 參數，而另一個具有 `out` 參數，則編譯器會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-116">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out` parameter.</span></span> <span data-ttu-id="ea9c7-117">例如，下列程式碼不會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-117">The following code, for example, doesn't compile.</span></span>  
  
 <span data-ttu-id="ea9c7-118">[!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ea9c7-118">[!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_2.cs)]</span></span>  
  
 <span data-ttu-id="ea9c7-119">不過，當一種方法具有 `ref` 或 `out` 參數，而另一種方法具有實值參數時，可以完成多載，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-119">However, overloading can be done when one method has a `ref` or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>  
  
 <span data-ttu-id="ea9c7-120">[!code-cs[csrefKeywordsMethodParams#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ea9c7-120">[!code-cs[csrefKeywordsMethodParams#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_3.cs)]</span></span>  
  
 <span data-ttu-id="ea9c7-121">在需要簽章比對的其他情況 (如隱藏或覆寫) 下，`ref` 和 `out` 是簽章的一部分，而且彼此不相符。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-121">In other situations that require signature matching, such as hiding or overriding, `ref` and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="ea9c7-122">屬性不是變數。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-122">Properties are not variables.</span></span> <span data-ttu-id="ea9c7-123">它們都是方法，且不能傳遞給 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-123">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="ea9c7-124">如需如何傳遞陣列的資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-124">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="ea9c7-125">您不能將 `ref` 和 `out` 關鍵字用於下列幾種方法：</span><span class="sxs-lookup"><span data-stu-id="ea9c7-125">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="ea9c7-126">使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-126">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="ea9c7-127">iterator 方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-127">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea9c7-128">範例</span><span class="sxs-lookup"><span data-stu-id="ea9c7-128">Example</span></span>  
 <span data-ttu-id="ea9c7-129">前一個範例會示範當您由參考傳遞實值類型時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-129">The previous examples demonstrate what happens when you pass value types by reference.</span></span> <span data-ttu-id="ea9c7-130">您也可以使用 `ref` 關鍵字，來傳遞參考類型。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-130">You can also use the `ref` keyword to pass reference types.</span></span> <span data-ttu-id="ea9c7-131">由參考傳遞參考類型，可讓被呼叫的方法取代該參考參數所參考之呼叫方法中的物件。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-131">Passing a reference type by reference enables the called method to replace the object in the calling method to which the reference parameter refers.</span></span> <span data-ttu-id="ea9c7-132">物件的儲存位置會以參考參數值的方式，傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-132">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="ea9c7-133">如果您變更參數儲存位置中的值 (指向新的物件)，則也會變更呼叫端所參考的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-133">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="ea9c7-134">下列範例會以 `ref` 參數，傳遞參考類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-134">The following example passes an instance of a reference type as a `ref` parameter.</span></span> <span data-ttu-id="ea9c7-135">如需如何依傳值和依傳址方式來傳遞參考類型的詳細資訊，請參閱[傳遞參考類型參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9c7-135">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>  
  
 <span data-ttu-id="ea9c7-136">[!code-cs[csrefKeywordsMethodParams#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="ea9c7-136">[!code-cs[csrefKeywordsMethodParams#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ea9c7-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ea9c7-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ea9c7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea9c7-138">See Also</span></span>  
 <span data-ttu-id="ea9c7-139">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea9c7-139">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="ea9c7-140"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea9c7-140"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="ea9c7-141"> [傳遞參數](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="ea9c7-141"> [Passing Parameters](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span></span>  
<span data-ttu-id="ea9c7-142"> [方法參數](../../../csharp/language-reference/keywords/method-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="ea9c7-142"> [Method Parameters](../../../csharp/language-reference/keywords/method-parameters.md) </span></span>  
<span data-ttu-id="ea9c7-143"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)</span><span class="sxs-lookup"><span data-stu-id="ea9c7-143"> [C# Keywords](../../../csharp/language-reference/keywords/index.md)</span></span>
