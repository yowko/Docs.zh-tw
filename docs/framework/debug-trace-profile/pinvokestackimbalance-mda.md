---
title: pInvokeStackImbalance MDA
description: 檢查 PInvokeStackImbalance MDA，這在進行或遵循平台叫用呼叫時，可能會在存取違規或記憶體損毀期間啟用。
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
ms.openlocfilehash: 89afd3fce3f2a8bffe88d45991ceeb59fc5e5b76
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803660"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="b19e6-103">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="b19e6-103">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="b19e6-104">`PInvokeStackImbalance`當 CLR 偵測到平台叫用呼叫之後的堆疊深度不符合預期的堆疊深度時，就會啟動 managed 偵錯工具（MDA），前提是屬性中指定的呼叫慣例 <xref:System.Runtime.InteropServices.DllImportAttribute> 和 managed 簽章中的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="b19e6-104">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="b19e6-105">`PInvokeStackImbalance` MDA 只會在 32 位元 x86 平台上實作。</span><span class="sxs-lookup"><span data-stu-id="b19e6-105">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="b19e6-106">`PInvokeStackImbalance`預設會停用 MDA。</span><span class="sxs-lookup"><span data-stu-id="b19e6-106">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="b19e6-107">在 Visual Studio 2017 和更新版本中， `PInvokeStackImbalance` MDA 會出現在 [**例外狀況設定**] 對話方塊的 [ **Managed 調試助理**] 清單中（當您選取 [ **Debug**  >  **Windows**  >  **例外狀況設定**] 時顯示）。</span><span class="sxs-lookup"><span data-stu-id="b19e6-107">In Visual Studio 2017 and later versions, the `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="b19e6-108">不過，選取或清除 [擲回**時中斷**] 核取方塊並不會啟用或停用 MDA。它只會控制 Visual Studio 在啟動 MDA 時是否擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b19e6-108">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="b19e6-109">徵狀</span><span class="sxs-lookup"><span data-stu-id="b19e6-109">Symptoms</span></span>

<span data-ttu-id="b19e6-110">應用程式在進行平台叫用呼叫期間或之後發生存取違規或記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="b19e6-110">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="b19e6-111">原因</span><span class="sxs-lookup"><span data-stu-id="b19e6-111">Cause</span></span>

<span data-ttu-id="b19e6-112">平台叫用呼叫的 Managed 簽章可能與所呼叫之方法的 Unmanaged 簽章不符。</span><span class="sxs-lookup"><span data-stu-id="b19e6-112">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="b19e6-113">當 Managed 簽章未宣告正確的參數數目，或未指定適當的參數大小時，便會造成這種不相符狀況。</span><span class="sxs-lookup"><span data-stu-id="b19e6-113">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="b19e6-114">MDA 也可能由於呼叫慣例 (可能由 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性指定) 與 Unmanaged 呼叫慣例不符而啟動。</span><span class="sxs-lookup"><span data-stu-id="b19e6-114">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="b19e6-115">解決方案</span><span class="sxs-lookup"><span data-stu-id="b19e6-115">Resolution</span></span>

<span data-ttu-id="b19e6-116">檢閱 Managed 平台叫用簽章和呼叫慣例，確認其與原生目標的簽章和呼叫慣例相符。</span><span class="sxs-lookup"><span data-stu-id="b19e6-116">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="b19e6-117">嘗試明確指定 Managed 和 Unmanaged 端的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="b19e6-117">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="b19e6-118">Unmanaged 函式也可能 (雖然可能性不高) 因其他一些原因而使堆疊失去平衡，例如 Unmanaged 編譯器中的 Bug。</span><span class="sxs-lookup"><span data-stu-id="b19e6-118">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="b19e6-119">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="b19e6-119">Effect on the Runtime</span></span>

<span data-ttu-id="b19e6-120">強制所有平台叫用呼叫採用 CLR 中未最佳化的路徑。</span><span class="sxs-lookup"><span data-stu-id="b19e6-120">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="b19e6-121">輸出</span><span class="sxs-lookup"><span data-stu-id="b19e6-121">Output</span></span>

<span data-ttu-id="b19e6-122">MDA 訊息會提供使堆疊失去平衡之平台叫用方法呼叫的名稱。</span><span class="sxs-lookup"><span data-stu-id="b19e6-122">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="b19e6-123">`SampleMethod` 方法之平台叫用呼叫的範例訊息為：</span><span class="sxs-lookup"><span data-stu-id="b19e6-123">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="b19e6-124">**對 PInvoke 函數 ' Sampleobject.samplemethod ' 的呼叫具有不對稱的堆疊。這很可能是因為受控 PInvoke 簽章與非受控目標籤章不相符。檢查 PInvoke 簽章的呼叫慣例和參數是否符合目標非受控簽章。**</span><span class="sxs-lookup"><span data-stu-id="b19e6-124">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="b19e6-125">組態</span><span class="sxs-lookup"><span data-stu-id="b19e6-125">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="b19e6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b19e6-126">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="b19e6-127">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="b19e6-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b19e6-128">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="b19e6-128">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
