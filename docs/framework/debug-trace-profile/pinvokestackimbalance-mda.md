---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc4a48c79fc39b12f8231bd913b4ca8970c0f46f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052359"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="cdc75-102">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="cdc75-102">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="cdc75-103">當 CLR 偵測到平台叫用呼叫之後的堆疊深度不符合預期的堆疊深度時，就會啟動<xref:System.Runtime.InteropServices.DllImportAttribute> managed偵錯工具（MDA），前提是屬性中指定的呼叫慣例和`PInvokeStackImbalance`managed 簽章中的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="cdc75-103">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="cdc75-104">`PInvokeStackImbalance` MDA 只會在 32 位元 x86 平台上實作。</span><span class="sxs-lookup"><span data-stu-id="cdc75-104">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="cdc75-105">預設會停用MDA。`PInvokeStackImbalance`</span><span class="sxs-lookup"><span data-stu-id="cdc75-105">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="cdc75-106">在 Visual Studio 2017 中， `PInvokeStackImbalance` MDA 會出現在 [**例外狀況設定**] 對話方塊的 [**受管理的調試助理**] 清單中（當您選取 [ **Debug**  >  **Windows**  >  **] 時，會顯示此方塊）例外狀況設定**）。</span><span class="sxs-lookup"><span data-stu-id="cdc75-106">In Visual Studio 2017, The `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="cdc75-107">不過，選取或清除 [擲回**時中斷**] 核取方塊並不會啟用或停用 MDA。它只會控制 Visual Studio 在啟動 MDA 時是否擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cdc75-107">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="cdc75-108">徵兆</span><span class="sxs-lookup"><span data-stu-id="cdc75-108">Symptoms</span></span>

<span data-ttu-id="cdc75-109">應用程式在進行平台叫用呼叫期間或之後發生存取違規或記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="cdc75-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="cdc75-110">原因</span><span class="sxs-lookup"><span data-stu-id="cdc75-110">Cause</span></span>

<span data-ttu-id="cdc75-111">平台叫用呼叫的 Managed 簽章可能與所呼叫之方法的 Unmanaged 簽章不符。</span><span class="sxs-lookup"><span data-stu-id="cdc75-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="cdc75-112">當 Managed 簽章未宣告正確的參數數目，或未指定適當的參數大小時，便會造成這種不相符狀況。</span><span class="sxs-lookup"><span data-stu-id="cdc75-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="cdc75-113">MDA 也可能由於呼叫慣例 (可能由 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性指定) 與 Unmanaged 呼叫慣例不符而啟動。</span><span class="sxs-lookup"><span data-stu-id="cdc75-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="cdc75-114">解決方式</span><span class="sxs-lookup"><span data-stu-id="cdc75-114">Resolution</span></span>

<span data-ttu-id="cdc75-115">檢閱 Managed 平台叫用簽章和呼叫慣例，確認其與原生目標的簽章和呼叫慣例相符。</span><span class="sxs-lookup"><span data-stu-id="cdc75-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="cdc75-116">嘗試明確指定 Managed 和 Unmanaged 端的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="cdc75-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="cdc75-117">Unmanaged 函式也可能 (雖然可能性不高) 因其他一些原因而使堆疊失去平衡，例如 Unmanaged 編譯器中的 Bug。</span><span class="sxs-lookup"><span data-stu-id="cdc75-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="cdc75-118">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="cdc75-118">Effect on the Runtime</span></span>

<span data-ttu-id="cdc75-119">強制所有平台叫用呼叫採用 CLR 中未最佳化的路徑。</span><span class="sxs-lookup"><span data-stu-id="cdc75-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="cdc75-120">Output</span><span class="sxs-lookup"><span data-stu-id="cdc75-120">Output</span></span>

<span data-ttu-id="cdc75-121">MDA 訊息會提供使堆疊失去平衡之平台叫用方法呼叫的名稱。</span><span class="sxs-lookup"><span data-stu-id="cdc75-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="cdc75-122">`SampleMethod` 方法之平台叫用呼叫的範例訊息為：</span><span class="sxs-lookup"><span data-stu-id="cdc75-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="cdc75-123">**對 PInvoke 函數 ' Sampleobject.samplemethod ' 的呼叫具有不對稱的堆疊。這很可能是因為受控 PInvoke 簽章與非受控目標籤章不相符。檢查 PInvoke 簽章的呼叫慣例和參數是否符合目標非受控簽章。**</span><span class="sxs-lookup"><span data-stu-id="cdc75-123">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="cdc75-124">組態</span><span class="sxs-lookup"><span data-stu-id="cdc75-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="cdc75-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdc75-125">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="cdc75-126">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="cdc75-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cdc75-127">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="cdc75-127">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
