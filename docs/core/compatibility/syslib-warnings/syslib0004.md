---
title: SYSLIB0004 警告
description: 瞭解產生編譯時期警告 SYSLIB0004 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 03be8bb54f71f74ed94ee2c3f8489397ae1e99b5
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596463"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="ae08c-103">SYSLIB0004：不支援 (CER) 功能的限制執列區域</span><span class="sxs-lookup"><span data-stu-id="ae08c-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="ae08c-104">只有在 .NET Framework 中才支援 [ (CER) 功能的受限制執列區域 ](../../../framework/performance/constrained-execution-regions.md) 。</span><span class="sxs-lookup"><span data-stu-id="ae08c-104">The [Constrained execution regions (CER)](../../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="ae08c-105">因此，從 .NET 5.0 開始，會將各種 CER 相關的 Api 標記為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="ae08c-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="ae08c-106">使用這些 Api `SYSLIB0004` 時，會在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="ae08c-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="ae08c-107">下列 CER 相關的 Api 已淘汰：</span><span class="sxs-lookup"><span data-stu-id="ae08c-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="ae08c-108">因應措施</span><span class="sxs-lookup"><span data-stu-id="ae08c-108">Workarounds</span></span>

- <span data-ttu-id="ae08c-109">如果您已將 CER 屬性套用至方法，請移除該屬性。</span><span class="sxs-lookup"><span data-stu-id="ae08c-109">If you have applied a CER attribute to a method, remove the attribute.</span></span> <span data-ttu-id="ae08c-110">這些屬性在 .NET 5.0 和更新版本中不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="ae08c-110">These attributes have no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  // REMOVE the attribute below.
  [ReliabilityContract(Consistency.WillNotCorruptState, Cer.Success)]
  public void DoSomething()
  {
  }

  // REMOVE the attribute below.
  [PrePrepareMethod]
  public void DoSomething()
  {
  }
  ```

- <span data-ttu-id="ae08c-111">如果您呼叫 `RuntimeHelpers.ProbeForSufficientStack` 或 `RuntimeHelpers.PrepareContractedDelegate` ，請移除呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae08c-111">If you are calling `RuntimeHelpers.ProbeForSufficientStack` or `RuntimeHelpers.PrepareContractedDelegate`, remove the call.</span></span> <span data-ttu-id="ae08c-112">這些呼叫在 .NET 5.0 和更新版本中不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="ae08c-112">These calls have no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  public void DoSomething()
  {
      // REMOVE the call below.
      RuntimeHelpers.ProbeForSufficientStack();

      // (Remainder of your method logic here.)
  }
  ```

- <span data-ttu-id="ae08c-113">如果您正在呼叫 `RuntimeHelpers.PrepareConstrainedRegions` ，請移除呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae08c-113">If you are calling `RuntimeHelpers.PrepareConstrainedRegions`, remove the call.</span></span> <span data-ttu-id="ae08c-114">此呼叫在 .NET 5.0 和更新版本中不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="ae08c-114">This call has no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  public void DoSomething_Old()
  {
      // REMOVE the call below.
      RuntimeHelpers.PrepareConstrainedRegions();
      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }

  public void DoSomething_Corrected()
  {
      // There is no call to PrepareConstrainedRegions. It's a normal try / finally block.

      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

- <span data-ttu-id="ae08c-115">如果您正在呼叫 `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup` ，請使用標準 _try/catch/finally_ 區塊來取代呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae08c-115">If you are calling `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup`, replace the call with a standard _try / catch / finally_ block.</span></span>

  ```csharp
  // The sample below produces warning SYSLIB0004.
  public void DoSomething_Old()
  {
      RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(MyTryCode, MyCleanupCode, null);
  }
  public void MyTryCode(object state) { /* try code */ }
  public void MyCleanupCode(object state, bool exceptionThrown) { /* cleanup code */ }

  // The corrected sample below does not produce warning SYSLIB0004.
  public void DoSomething_Corrected()
  {
      try
      {
          // try code
      }
      catch (Exception ex)
      {
          // exception handling code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="ae08c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae08c-116">See also</span></span>

- [<span data-ttu-id="ae08c-117">限制的執列區域</span><span class="sxs-lookup"><span data-stu-id="ae08c-117">Constrained execution regions</span></span>](../../../framework/performance/constrained-execution-regions.md)
