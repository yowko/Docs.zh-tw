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
# <a name="threadabort-is-obsolete"></a><span data-ttu-id="58c3d-103">執行緒。中止已淘汰</span><span class="sxs-lookup"><span data-stu-id="58c3d-103">Thread.Abort is obsolete</span></span>

<span data-ttu-id="58c3d-104"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Api 已淘汰。</span><span class="sxs-lookup"><span data-stu-id="58c3d-104">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="58c3d-105">如果呼叫這些方法，以 .NET 5.0 或更新版本為目標的專案將會遇到編譯時間警告 `SYSLIB0006` 。</span><span class="sxs-lookup"><span data-stu-id="58c3d-105">Projects that target .NET 5.0 or a later version will encounter compile-time warning `SYSLIB0006` if these methods are called.</span></span>

## <a name="change-description"></a><span data-ttu-id="58c3d-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="58c3d-106">Change description</span></span>

<span data-ttu-id="58c3d-107">之前，的呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 不會產生編譯時期警告，不過，方法會 <xref:System.PlatformNotSupportedException> 在執行時間擲回。</span><span class="sxs-lookup"><span data-stu-id="58c3d-107">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="58c3d-108">從 .NET 5.0 開始， <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 會標示為「已淘汰」為「警告」。</span><span class="sxs-lookup"><span data-stu-id="58c3d-108">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="58c3d-109">呼叫這個方法會產生編譯器警告 `SYSLIB0006` 。</span><span class="sxs-lookup"><span data-stu-id="58c3d-109">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="58c3d-110">方法的執行方式不變，且會繼續擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="58c3d-110">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="58c3d-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="58c3d-111">Reason for change</span></span>

<span data-ttu-id="58c3d-112">假設 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> <xref:System.PlatformNotSupportedException> 在所有 .net 執行上一律會擲回，但 .NET Framework 除外，就 <xref:System.ObsoleteAttribute> 會將它新增至方法，以吸引人注意它的呼叫位置。</span><span class="sxs-lookup"><span data-stu-id="58c3d-112">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="58c3d-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="58c3d-113">Version introduced</span></span>

<span data-ttu-id="58c3d-114">5.0</span><span class="sxs-lookup"><span data-stu-id="58c3d-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="58c3d-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="58c3d-115">Recommended action</span></span>

- <span data-ttu-id="58c3d-116">使用 <xref:System.Threading.CancellationToken> 來中止工作單位的處理，而不是呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="58c3d-116">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58c3d-117">下列範例說明如何使用 <xref:System.Threading.CancellationToken> 。</span><span class="sxs-lookup"><span data-stu-id="58c3d-117">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

  <span data-ttu-id="58c3d-118">如需詳細資訊，請參閱 [managed 執行緒中的取消](../../../../standard/threading/cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="58c3d-118">For more information, see [Cancellation in managed threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="58c3d-119">若要隱藏編譯時期警告，請隱藏警告程式碼 `SYSLIB0006` 。</span><span class="sxs-lookup"><span data-stu-id="58c3d-119">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="58c3d-120">警告碼是特定的 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ，隱藏它不會隱藏程式碼中的其他 obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="58c3d-120">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="58c3d-121">不過，我們建議您移除的呼叫， <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 而不是隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="58c3d-121">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="58c3d-122">您也可以隱藏專案檔中的警告。</span><span class="sxs-lookup"><span data-stu-id="58c3d-122">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

## <a name="affected-apis"></a><span data-ttu-id="58c3d-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="58c3d-123">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
