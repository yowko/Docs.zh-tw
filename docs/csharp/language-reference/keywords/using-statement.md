---
title: "using 陳述式 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 201dde951b4f92d92b7d78b3d71a3f3cfb559507
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="using-statement-c-reference"></a><span data-ttu-id="b6e1f-102">using 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b6e1f-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="b6e1f-103">提供方便的語法，以確保正確使用 <xref:System.IDisposable> 物件。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e1f-104">範例</span><span class="sxs-lookup"><span data-stu-id="b6e1f-104">Example</span></span>  
 <span data-ttu-id="b6e1f-105">下列範例示範如何使用 using 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-105">The following example shows how to use the using statement.</span></span>  
  
 <span data-ttu-id="b6e1f-106">[!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b6e1f-106">[!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6e1f-107">備註</span><span class="sxs-lookup"><span data-stu-id="b6e1f-107">Remarks</span></span>  
 <span data-ttu-id="b6e1f-108"><xref:System.IO.File> 和 <xref:System.Drawing.Font> 是 Managed 類型的範例，這些類型會存取 Unmanaged 資源 (在本例中為檔案控制代碼和裝置內容)。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="b6e1f-109">還有許多其他類型的 Unmanaged 資源，以及封裝這些資源的類別庫類型。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="b6e1f-110">所有這些類型都會實作 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
 <span data-ttu-id="b6e1f-111">一般而言，當您使用 `IDisposable` 物件時，您應該在 `using` 陳述式中宣告並具現化該物件。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-111">As a rule, when you use an `IDisposable` object, you should declare and instantiate it in a `using` statement.</span></span> <span data-ttu-id="b6e1f-112">`using` 陳述式會以正確的方式呼叫物件上的 <xref:System.IDisposable.Dispose%2A> 方法，而且 (當您如稍早所示使用它時) 它也會在一呼叫 <xref:System.IDisposable.Dispose%2A> 時讓物件本身超出範圍。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="b6e1f-113">在 `using` 區塊內，物件是唯讀的，而且無法加以修改或重新指派。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="b6e1f-114">`using` 陳述式可確保呼叫 <xref:System.IDisposable.Dispose%2A>，即使在您呼叫物件上的方法時發生例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs while you are calling methods on the object.</span></span> <span data-ttu-id="b6e1f-115">您可以將物件放在 try 區塊內，然後在 finally 區塊中呼叫 <xref:System.IDisposable.Dispose%2A>，來達到相同的結果；事實上，這就是編譯器轉譯 `using` 陳述式的方式。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-115">You can achieve the same result by putting the object inside a try block and then calling <xref:System.IDisposable.Dispose%2A> in a finally block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="b6e1f-116">稍早的程式碼範例會在編譯時期展開為下列程式碼 (注意額外的大括號是為了建立物件的有限範圍)：</span><span class="sxs-lookup"><span data-stu-id="b6e1f-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 <span data-ttu-id="b6e1f-117">[!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b6e1f-117">[!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]</span></span>  
  
 <span data-ttu-id="b6e1f-118">您可以在 `using` 陳述式中宣告一種類型的多個執行個體，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-118">Multiple instances of a type can be declared in a `using` statement, as shown in the following example.</span></span>  
  
 <span data-ttu-id="b6e1f-119">[!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="b6e1f-119">[!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]</span></span>  
  
 <span data-ttu-id="b6e1f-120">您可以具現化資源物件，然後將變數傳遞至 `using` 陳述式，但這不是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-120">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="b6e1f-121">在此情況下，物件會在控制權離開 `using` 區塊之後留在範圍內，不過它可能無法再存取其 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-121">In this case, the object remains in scope after control leaves the `using` block even though it will probably no longer have access to its unmanaged resources.</span></span> <span data-ttu-id="b6e1f-122">換句話說，您再也無法將它完整初始化。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-122">In other words, it will no longer be fully initialized.</span></span> <span data-ttu-id="b6e1f-123">如果您嘗試在 `using` 區塊外部使用該物件，則會有導致擲回例外狀況的風險。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-123">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="b6e1f-124">因此，通常最好在 `using` 陳述式中具現化物件，並將其範圍限制為 `using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="b6e1f-124">For this reason, it is generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 <span data-ttu-id="b6e1f-125">[!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="b6e1f-125">[!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b6e1f-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b6e1f-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b6e1f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6e1f-127">See Also</span></span>  
 <span data-ttu-id="b6e1f-128">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b6e1f-128">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b6e1f-129">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b6e1f-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b6e1f-130">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b6e1f-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b6e1f-131">[using 指示詞](../../../csharp/language-reference/keywords/using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="b6e1f-131">[using Directive](../../../csharp/language-reference/keywords/using-directive.md) </span></span>  
 <span data-ttu-id="b6e1f-132">[記憶體回收](../../../standard/garbage-collection/index.md) </span><span class="sxs-lookup"><span data-stu-id="b6e1f-132">[Garbage Collection](../../../standard/garbage-collection/index.md) </span></span>  
 [<span data-ttu-id="b6e1f-133">實作 Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="b6e1f-133">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)

