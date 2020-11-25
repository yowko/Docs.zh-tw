---
title: 中斷性變更：執行緒. 中止已淘汰
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中的執行緒. 中止 Api 已過時。
ms.date: 11/01/2020
ms.openlocfilehash: 6d7dfce8fda393bfd88c9b4cf0c59d53942cee25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760456"
---
# <a name="threadabort-is-obsolete"></a>執行緒。中止已淘汰

<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Api 已淘汰。 如果呼叫這些方法，以 .NET 5.0 或更新版本為目標的專案將會遇到編譯時間警告 `SYSLIB0006` 。

## <a name="change-description"></a>變更描述

之前，的呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 不會產生編譯時期警告，不過，方法會 <xref:System.PlatformNotSupportedException> 在執行時間擲回。

從 .NET 5.0 開始， <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 會標示為「已淘汰」為「警告」。 呼叫這個方法會產生編譯器警告 `SYSLIB0006` 。 方法的執行方式不變，且會繼續擲回 <xref:System.PlatformNotSupportedException> 。

## <a name="reason-for-change"></a>變更的原因

假設 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> <xref:System.PlatformNotSupportedException> 在所有 .net 執行上一律會擲回，但 .NET Framework 除外，就 <xref:System.ObsoleteAttribute> 會將它新增至方法，以吸引人注意它的呼叫位置。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

- 使用 <xref:System.Threading.CancellationToken> 來中止工作單位的處理，而不是呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 。 下列範例說明如何使用 <xref:System.Threading.CancellationToken> 。

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

  如需詳細資訊，請參閱 [managed 執行緒中的取消](../../../../standard/threading/cancellation-in-managed-threads.md)。

- 若要隱藏編譯時期警告，請隱藏警告程式碼 `SYSLIB0006` 。 警告碼是特定的 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ，隱藏它不會隱藏程式碼中的其他 obsoletion 警告。 不過，我們建議您移除的呼叫， <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 而不是隱藏警告。

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  您也可以隱藏專案檔中的警告。

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
