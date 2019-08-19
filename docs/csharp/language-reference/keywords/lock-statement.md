---
title: lock 陳述式 - C# 參考
ms.custom: seodec18
description: 使用 C# lock 陳述式，來同步處理執行緒對共用資源的存取
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 7ae19e48467bf5feca115c993c2299c1ecbaadc7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566341"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="a372a-103">lock 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a372a-103">lock statement (C# reference)</span></span>

<span data-ttu-id="a372a-104">`lock` 陳述式會取得指定物件的互斥鎖定、執行陳述式區塊，然後釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="a372a-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="a372a-105">持有鎖定時，持有鎖定的執行緒可以再次取得並釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="a372a-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="a372a-106">其他執行緒將無法取得鎖定，並將等待直到釋放鎖定為止。</span><span class="sxs-lookup"><span data-stu-id="a372a-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="a372a-107">`lock` 陳述式格式為</span><span class="sxs-lookup"><span data-stu-id="a372a-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="a372a-108">`x` 是[參考型別](reference-types.md)的運算式。</span><span class="sxs-lookup"><span data-stu-id="a372a-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="a372a-109">其完全等同於</span><span class="sxs-lookup"><span data-stu-id="a372a-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="a372a-110">由於程式碼會使用 [try...finally](try-finally.md) 區塊，即使在 `lock` 陳述式的主體內擲回例外狀況，也會釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="a372a-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="a372a-111">您不能在 `lock` 陳述式主體中使用 [await](await.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a372a-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="a372a-112">備註</span><span class="sxs-lookup"><span data-stu-id="a372a-112">Remarks</span></span>

<span data-ttu-id="a372a-113">當您同步處理執行緒對共用資源的存取時，請鎖定專用物件執行個體 (例如 `private readonly object balanceLock = new object();`) 或另一個不太可能由程式碼不相關的部分用作鎖定物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a372a-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="a372a-114">避免對不同的共用資源使用相同的鎖定物件執行個體，因為其可能導致鎖死或鎖定爭用。</span><span class="sxs-lookup"><span data-stu-id="a372a-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="a372a-115">尤其要避免使用下列項目當作鎖定物件：</span><span class="sxs-lookup"><span data-stu-id="a372a-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="a372a-116">`this`，呼叫者可能會將其作為鎖定。</span><span class="sxs-lookup"><span data-stu-id="a372a-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="a372a-117"><xref:System.Type> 執行個體，因為這些可能會由 [typeof](../operators/type-testing-and-cast.md#typeof-operator) 運算子或反映取得。</span><span class="sxs-lookup"><span data-stu-id="a372a-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="a372a-118">字串執行個體 (包括字串常值)，因為那些可能會[暫留](/dotnet/api/system.string.intern#remarks)。</span><span class="sxs-lookup"><span data-stu-id="a372a-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="a372a-119">範例</span><span class="sxs-lookup"><span data-stu-id="a372a-119">Example</span></span>

<span data-ttu-id="a372a-120">下列範例會定義 `Account` 類別，該類別會透過鎖定專用的 `balanceLock` 執行個體來同步對其私用 `balance` 欄位的存取。</span><span class="sxs-lookup"><span data-stu-id="a372a-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="a372a-121">使用相同的執行個體進行鎖定，可確保嘗試同時呼叫 `Debit` 或 `Credit` 方法的兩個執行緒無法同時更新 `balance` 欄位。</span><span class="sxs-lookup"><span data-stu-id="a372a-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="a372a-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a372a-122">C# language specification</span></span>

<span data-ttu-id="a372a-123">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [lock 陳述式](~/_csharplang/spec/statements.md#the-lock-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="a372a-123">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a372a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a372a-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="a372a-125">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a372a-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a372a-126">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a372a-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="a372a-127">同步處理原始物件概觀</span><span class="sxs-lookup"><span data-stu-id="a372a-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
