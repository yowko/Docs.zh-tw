---
title: SYSLIB0006 警告
description: 瞭解產生編譯時期警告 SYSLIB0006 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 45d2d8ec6ad99996f8b8f46d0c2e0ac2e02cf450
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333251"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="64827-103">SYSLIB0006：不支援 Thread. Abort</span><span class="sxs-lookup"><span data-stu-id="64827-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="64827-104">下列 Api 會標示為已淘汰，從 .NET 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="64827-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="64827-105">使用這些 Api `SYSLIB0006` 時，會在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="64827-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workaround"></a><span data-ttu-id="64827-106">因應措施</span><span class="sxs-lookup"><span data-stu-id="64827-106">Workaround</span></span>

<span data-ttu-id="64827-107">使用 <xref:System.Threading.CancellationToken> 來中止工作單位的處理，而不是呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="64827-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="64827-108">下列範例說明如何使用 <xref:System.Threading.CancellationToken> 。</span><span class="sxs-lookup"><span data-stu-id="64827-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

```csharp
void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
{
    if (QueryIsMoreWorkPending())
    {
        // If the CancellationToken is marked as "needs to cancel",
        // this will throw the appropriate exception.
        cancellationToken.ThrowIfCancellationRequested();

        WorkItem work = DequeueWorkItem();
        ProcessWorkItem(work);
    }
}
```

## <a name="see-also"></a><span data-ttu-id="64827-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="64827-109">See also</span></span>

- [<span data-ttu-id="64827-110">執行緒。 Abort 是過時的重大變更</span><span class="sxs-lookup"><span data-stu-id="64827-110">Thread.Abort is obsolete - breaking change</span></span>](3.1-5.0.md#threadabort-is-obsolete)
- [<span data-ttu-id="64827-111">受控執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="64827-111">Cancellation in managed threads</span></span>](../../standard/threading/cancellation-in-managed-threads.md)
