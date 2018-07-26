---
title: lock 陳述式 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960948"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="4e769-102">lock 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4e769-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="4e769-103">`lock` 關鍵字可藉由取得指定物件的互斥鎖定、執行陳述式，然後釋放鎖定，以將陳述式區塊標示為關鍵區段。</span><span class="sxs-lookup"><span data-stu-id="4e769-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="4e769-104">下列範例包括 `lock` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4e769-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="4e769-105">如需詳細資訊，請參閱[執行緒同步處理](../../programming-guide/concepts/threading/thread-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="4e769-105">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e769-106">備註</span><span class="sxs-lookup"><span data-stu-id="4e769-106">Remarks</span></span>  
 <span data-ttu-id="4e769-107">`lock` 關鍵字可確保當關鍵區段中已有執行緒時，另一個執行緒不會進入程式碼的關鍵區段。</span><span class="sxs-lookup"><span data-stu-id="4e769-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="4e769-108">如果另一個執行緒嘗試進入鎖定的程式碼，它將會等候、封鎖，直到釋放物件。</span><span class="sxs-lookup"><span data-stu-id="4e769-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="4e769-109">[執行緒](../../programming-guide/concepts/threading/index.md)一節說明執行緒的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4e769-109">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>  
  
 <span data-ttu-id="4e769-110">`lock` 關鍵字會在區塊開頭呼叫 <xref:System.Threading.Monitor.Enter%2A>，在區塊結尾呼叫 <xref:System.Threading.Monitor.Exit%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e769-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="4e769-111">如果 <xref:System.Threading.Thread.Interrupt%2A> 插斷的執行緒正在等候進入 `lock` 陳述式，便會擲回 <xref:System.Threading.ThreadInterruptedException>。</span><span class="sxs-lookup"><span data-stu-id="4e769-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="4e769-112">一般情況下，請避免鎖定 `public` 類型，或超出程式碼控制範圍的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e769-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="4e769-113">`lock (this)`、`lock (typeof (MyType))` 和 `lock ("myLock")` 等常見的建構函式則違反這項指導方針：</span><span class="sxs-lookup"><span data-stu-id="4e769-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="4e769-114">如果可以公開存取執行個體的話，`lock (this)` 會成為問題。</span><span class="sxs-lookup"><span data-stu-id="4e769-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="4e769-115">如果可以公開存取 `MyType` 的話，`lock (typeof (MyType))` 會成為問題。</span><span class="sxs-lookup"><span data-stu-id="4e769-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="4e769-116">由於處理序中使用相同字串的任何其他程式碼，將會共用相同的鎖定，因此 `lock("myLock")` 會成為問題。</span><span class="sxs-lookup"><span data-stu-id="4e769-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="4e769-117">最佳做法是定義要鎖定的 `private` 物件或 `private static` 物件變數，以保護通用於所有執行個體的資料。</span><span class="sxs-lookup"><span data-stu-id="4e769-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="4e769-118">您不能在 `lock` 陳述式主體中使用 [await](../../../csharp/language-reference/keywords/await.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4e769-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e769-119">範例</span><span class="sxs-lookup"><span data-stu-id="4e769-119">Example</span></span>  
 <span data-ttu-id="4e769-120">下列範例會示範執行緒的簡易使用方式，而不在 C# 中使用鎖定。</span><span class="sxs-lookup"><span data-stu-id="4e769-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="4e769-121">範例</span><span class="sxs-lookup"><span data-stu-id="4e769-121">Example</span></span>  
 <span data-ttu-id="4e769-122">下列範例會使用執行緒和 `lock`。</span><span class="sxs-lookup"><span data-stu-id="4e769-122">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="4e769-123">只要 `lock` 陳述式存在，則該陳述式區塊就是關鍵區段，且 `balance` 永遠不會是負數。</span><span class="sxs-lookup"><span data-stu-id="4e769-123">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4e769-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4e769-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e769-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e769-125">See Also</span></span>  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [<span data-ttu-id="4e769-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4e769-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4e769-127">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4e769-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4e769-128">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="4e769-128">Threading</span></span>](../../programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="4e769-129">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4e769-129">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4e769-130">陳述式關鍵字</span><span class="sxs-lookup"><span data-stu-id="4e769-130">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="4e769-131">Interlocked 作業</span><span class="sxs-lookup"><span data-stu-id="4e769-131">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="4e769-132">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="4e769-132">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="4e769-133">執行緒同步處理</span><span class="sxs-lookup"><span data-stu-id="4e769-133">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)
