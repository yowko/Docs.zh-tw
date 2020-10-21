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
# <a name="syslib0006-threadabort-is-not-supported"></a>SYSLIB0006：不支援 Thread. Abort

下列 Api 會標示為已淘汰，從 .NET 5.0 開始。 使用這些 Api `SYSLIB0006` 時，會在編譯時期產生警告。

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workaround"></a>因應措施

使用 <xref:System.Threading.CancellationToken> 來中止工作單位的處理，而不是呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 。 下列範例說明如何使用 <xref:System.Threading.CancellationToken> 。

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

## <a name="see-also"></a>請參閱

- [執行緒。 Abort 是過時的重大變更](3.1-5.0.md#threadabort-is-obsolete)
- [受控執行緒中的取消作業](../../standard/threading/cancellation-in-managed-threads.md)
