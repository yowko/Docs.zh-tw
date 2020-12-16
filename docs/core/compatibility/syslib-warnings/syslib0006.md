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
# <a name="syslib0006-threadabort-is-not-supported"></a>SYSLIB0006：不支援 Thread. Abort

下列 Api 會標示為已淘汰，從 .NET 5.0 開始。 使用這些 Api `SYSLIB0006` 時，會在編譯時期產生警告。

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a>因應措施

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

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>另請參閱

- [Thread.Abort 已過時](../core-libraries/5.0/thread-abort-obsolete.md)
- [受控執行緒中的取消作業](../../../standard/threading/cancellation-in-managed-threads.md)
