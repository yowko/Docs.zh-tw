---
title: SYSLIB0006 警告
description: 瞭解產生編譯時期警告 SYSLIB0006 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: c1eecade9280ac37917bc24aa2973756c7f08d87
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596460"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="717d5-103">SYSLIB0006：不支援 Thread. Abort</span><span class="sxs-lookup"><span data-stu-id="717d5-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="717d5-104">下列 Api 會標示為已淘汰，從 .NET 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="717d5-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="717d5-105">使用這些 Api `SYSLIB0006` 時，會在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="717d5-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="717d5-106">因應措施</span><span class="sxs-lookup"><span data-stu-id="717d5-106">Workarounds</span></span>

<span data-ttu-id="717d5-107">使用 <xref:System.Threading.CancellationToken> 來中止工作單位的處理，而不是呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="717d5-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="717d5-108">下列範例說明如何使用 <xref:System.Threading.CancellationToken> 。</span><span class="sxs-lookup"><span data-stu-id="717d5-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="717d5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="717d5-109">See also</span></span>

- [<span data-ttu-id="717d5-110">Thread.Abort 已過時</span><span class="sxs-lookup"><span data-stu-id="717d5-110">Thread.Abort is obsolete</span></span>](../core-libraries/5.0/thread-abort-obsolete.md)
- [<span data-ttu-id="717d5-111">受控執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="717d5-111">Cancellation in managed threads</span></span>](../../../standard/threading/cancellation-in-managed-threads.md)
