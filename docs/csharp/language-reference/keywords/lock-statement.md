---
title: "lock 陳述式 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
dev_langs:
- CSharp
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
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
ms.openlocfilehash: 00dcbb9feec11587265bf61667d91c2c1598065b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="5d83f-102">lock 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5d83f-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="5d83f-103">`lock` 關鍵字可藉由取得指定物件的互斥鎖定、執行陳述式，然後釋放鎖定，以將陳述式區塊標示為關鍵區段。</span><span class="sxs-lookup"><span data-stu-id="5d83f-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="5d83f-104">下列範例包括 `lock` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5d83f-104">The following example includes a `lock` statement.</span></span>  
  
```csharp  
class Account  
{  
    decimal balance;  
    private Object thisLock = new Object();  
  
    public void Withdraw(decimal amount)  
    {  
        lock (thisLock)  
        {  
            if (amount > balance)  
            {  
                throw new Exception("Insufficient funds");  
            }  
            balance -= amount;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="5d83f-105">如需詳細資訊，請參閱[執行緒同步處理](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)。</span><span class="sxs-lookup"><span data-stu-id="5d83f-105">For more information, see [Thread Synchronization](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d83f-106">備註</span><span class="sxs-lookup"><span data-stu-id="5d83f-106">Remarks</span></span>  
 <span data-ttu-id="5d83f-107">`lock` 關鍵字可確保當關鍵區段中已有執行緒時，另一個執行緒不會進入程式碼的關鍵區段。</span><span class="sxs-lookup"><span data-stu-id="5d83f-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="5d83f-108">如果另一個執行緒嘗試進入鎖定的程式碼，它將會等候、封鎖，直到釋放物件。</span><span class="sxs-lookup"><span data-stu-id="5d83f-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="5d83f-109">[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)一節說明執行緒的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5d83f-109">The section [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) discusses threading.</span></span>  
  
 <span data-ttu-id="5d83f-110">`lock` 關鍵字會在區塊開頭呼叫 <xref:System.Threading.Monitor.Enter%2A>，在區塊結尾呼叫 <xref:System.Threading.Monitor.Exit%2A>。</span><span class="sxs-lookup"><span data-stu-id="5d83f-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="5d83f-111">如果 <xref:System.Threading.Thread.Interrupt%2A> 插斷的執行緒正在等候進入 `lock` 陳述式，便會擲回 <xref:System.Threading.ThreadInterruptedException>。</span><span class="sxs-lookup"><span data-stu-id="5d83f-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="5d83f-112">一般情況下，請避免鎖定 `public` 類型，或超出程式碼控制範圍的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5d83f-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="5d83f-113">`lock (this)`、`lock (typeof (MyType))` 和 `lock ("myLock")` 等常見的建構函式則違反這項指導方針：</span><span class="sxs-lookup"><span data-stu-id="5d83f-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="5d83f-114">如果可以公開存取執行個體的話，`lock (this)` 會成為問題。</span><span class="sxs-lookup"><span data-stu-id="5d83f-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="5d83f-115">如果可以公開存取 `MyType` 的話，`lock (typeof (MyType))` 會成為問題。</span><span class="sxs-lookup"><span data-stu-id="5d83f-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="5d83f-116">由於處理序中使用相同字串的任何其他程式碼，將會共用相同的鎖定，因此 `lock("myLock")` 會成為問題。</span><span class="sxs-lookup"><span data-stu-id="5d83f-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="5d83f-117">最佳做法是定義要鎖定的 `private` 物件或 `private static` 物件變數，以保護通用於所有執行個體的資料。</span><span class="sxs-lookup"><span data-stu-id="5d83f-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="5d83f-118">您不能在 `lock` 陳述式主體中使用 [await](../../../csharp/language-reference/keywords/await.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5d83f-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d83f-119">範例</span><span class="sxs-lookup"><span data-stu-id="5d83f-119">Example</span></span>  
 <span data-ttu-id="5d83f-120">下列範例會示範執行緒的簡易使用方式，而不在 C# 中使用鎖定。</span><span class="sxs-lookup"><span data-stu-id="5d83f-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 <span data-ttu-id="5d83f-121">[!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5d83f-121">[!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d83f-122">範例</span><span class="sxs-lookup"><span data-stu-id="5d83f-122">Example</span></span>  
 <span data-ttu-id="5d83f-123">下列範例會使用執行緒和 `lock`。</span><span class="sxs-lookup"><span data-stu-id="5d83f-123">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="5d83f-124">只要 `lock` 陳述式存在，則該陳述式區塊就是關鍵區段，且 `balance` 永遠不會是負數。</span><span class="sxs-lookup"><span data-stu-id="5d83f-124">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 <span data-ttu-id="5d83f-125">[!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5d83f-125">[!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5d83f-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5d83f-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d83f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d83f-127">See Also</span></span>  
 <span data-ttu-id="5d83f-128"><xref:System.Reflection.MethodImplAttributes></span><span class="sxs-lookup"><span data-stu-id="5d83f-128"><xref:System.Reflection.MethodImplAttributes></span></span>   
 <span data-ttu-id="5d83f-129"><xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="5d83f-129"><xref:System.Threading.Mutex></span></span>   
 <span data-ttu-id="5d83f-130">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5d83f-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="5d83f-131">[C# 程式設計指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5d83f-131">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5d83f-132">[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) </span><span class="sxs-lookup"><span data-stu-id="5d83f-132">[Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) </span></span>  
 <span data-ttu-id="5d83f-133">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="5d83f-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="5d83f-134">[陳述式關鍵字](../../../csharp/language-reference/keywords/statement-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="5d83f-134">[Statement Keywords](../../../csharp/language-reference/keywords/statement-keywords.md) </span></span>  
 <span data-ttu-id="5d83f-135">@System.Threading.Monitor</span><span class="sxs-lookup"><span data-stu-id="5d83f-135">@System.Threading.Monitor</span></span>   
 <span data-ttu-id="5d83f-136">[Interlocked 作業](../../../standard/threading/interlocked-operations.md) </span><span class="sxs-lookup"><span data-stu-id="5d83f-136">[Interlocked Operations](../../../standard/threading/interlocked-operations.md) </span></span>  
 <span data-ttu-id="5d83f-137">[AutoResetEvent](../../../standard/threading/autoresetevent.md) </span><span class="sxs-lookup"><span data-stu-id="5d83f-137">[AutoResetEvent](../../../standard/threading/autoresetevent.md) </span></span>  
 [<span data-ttu-id="5d83f-138">執行緒同步處理</span><span class="sxs-lookup"><span data-stu-id="5d83f-138">Thread Synchronization</span></span>](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)

