---
title: lock 陳述式 (C# 參考)
description: 使用 C# 鎖定陳述式，將執行緒存取同步至共用資源
ms.date: 08/28/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2b6fbfb2f81d7745c4effb9ea0087f34cc872a6c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858352"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="97c3e-103">lock 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="97c3e-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="97c3e-104">`lock` 陳述式可取得所指定物件的互斥鎖定、執行陳述式鎖定，然後釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="97c3e-104">The `lock` statement obtains the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="97c3e-105">持有鎖定時，持有鎖定的執行緒可以再次取得並釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="97c3e-105">While a lock is held, the thread that holds the lock can again obtain and release the lock.</span></span> <span data-ttu-id="97c3e-106">其他執行緒將無法取得鎖定，並將等待直到釋放鎖定為止。</span><span class="sxs-lookup"><span data-stu-id="97c3e-106">Any other thread is blocked from obtaining the lock and waits until the lock is released.</span></span>

<span data-ttu-id="97c3e-107">`lock` 陳述式格式為</span><span class="sxs-lookup"><span data-stu-id="97c3e-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="97c3e-108">`x` 是[參考型別](reference-types.md)的運算式。</span><span class="sxs-lookup"><span data-stu-id="97c3e-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="97c3e-109">其完全等同於</span><span class="sxs-lookup"><span data-stu-id="97c3e-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="97c3e-110">由於程式碼會使用 [try...finally](try-finally.md) 區塊，即使在 `lock` 陳述式的主體內擲回例外狀況，也會釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="97c3e-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="97c3e-111">您不能在 `lock` 陳述式主體中使用 [await](await.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="97c3e-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="97c3e-112">備註</span><span class="sxs-lookup"><span data-stu-id="97c3e-112">Remarks</span></span>

<span data-ttu-id="97c3e-113">當您將執行緒存取同步至共用資源時，請鎖定專用物件執行個體 (例如 `private readonly object balanceLock = new object();`) 或另一個不太可能由程式碼不相關的部分用作鎖定物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="97c3e-113">When you synchronize thread access to shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="97c3e-114">避免對不同的共用資源使用相同的鎖定物件執行個體，因為其可能導致鎖死或鎖定爭用。</span><span class="sxs-lookup"><span data-stu-id="97c3e-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="97c3e-115">特別是，請避免使用</span><span class="sxs-lookup"><span data-stu-id="97c3e-115">In particular, avoid using</span></span>

- <span data-ttu-id="97c3e-116">`this` (呼叫者可能會將其作為鎖定)、</span><span class="sxs-lookup"><span data-stu-id="97c3e-116">`this` (might be used by the callers as a lock),</span></span>
- <span data-ttu-id="97c3e-117"><xref:System.Type> 執行個體 (可能會由 [typeof](typeof.md) 運算子或反映取得)、</span><span class="sxs-lookup"><span data-stu-id="97c3e-117"><xref:System.Type> instances (might be obtained by the [typeof](typeof.md) operator or reflection),</span></span>
- <span data-ttu-id="97c3e-118">字串執行個體，包括字串常值、</span><span class="sxs-lookup"><span data-stu-id="97c3e-118">string instances, including string literals,</span></span>

<span data-ttu-id="97c3e-119">作為鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="97c3e-119">as lock objects.</span></span>

## <a name="example"></a><span data-ttu-id="97c3e-120">範例</span><span class="sxs-lookup"><span data-stu-id="97c3e-120">Example</span></span>

<span data-ttu-id="97c3e-121">下列範例會定義 `Account` 類別，該類別會透過鎖定專用的 `balanceLock` 執行個體來同步對其私用 `balance` 欄位的存取。</span><span class="sxs-lookup"><span data-stu-id="97c3e-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="97c3e-122">使用相同的執行個體進行鎖定，可確保嘗試同時呼叫 `Debit` 或 `Credit` 方法的兩個執行緒無法同時更新 `balance` 欄位。</span><span class="sxs-lookup"><span data-stu-id="97c3e-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="97c3e-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="97c3e-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="97c3e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97c3e-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="97c3e-125">C# 參考</span><span class="sxs-lookup"><span data-stu-id="97c3e-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="97c3e-126">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="97c3e-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="97c3e-127">陳述式關鍵字</span><span class="sxs-lookup"><span data-stu-id="97c3e-127">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="97c3e-128">Interlocked 作業</span><span class="sxs-lookup"><span data-stu-id="97c3e-128">Interlocked operations</span></span>](../../../standard/threading/interlocked-operations.md)
- [<span data-ttu-id="97c3e-129">同步處理原始物件概觀</span><span class="sxs-lookup"><span data-stu-id="97c3e-129">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)