---
title: invalidVariant MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 64f5a4425d70974bae8c4f7bec28041e687fe95f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228480"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="94db6-102">invalidVariant MDA</span><span class="sxs-lookup"><span data-stu-id="94db6-102">invalidVariant MDA</span></span>
<span data-ttu-id="94db6-103">當從機器碼或 Unmanaged 程式碼呼叫至 Managed 程式碼時遇到無效的 `VARIANT` 結構，就會啟動 `invalidVariant` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="94db6-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="94db6-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="94db6-104">Symptoms</span></span>  
 <span data-ttu-id="94db6-105">在機器碼和 Managed 程式碼轉換期間的未預期行為，這會牽涉到封送處理 `VARIANT` 給物件。</span><span class="sxs-lookup"><span data-stu-id="94db6-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="94db6-106">原因</span><span class="sxs-lookup"><span data-stu-id="94db6-106">Cause</span></span>  
 <span data-ttu-id="94db6-107">機器碼傳遞格式不正確的 `VARIANT` 結構給 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="94db6-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="94db6-108">如果 `VARIANT` 無效，則執行階段嘗試封送處理 `VARIANT` 給物件，並啟動 MDA。</span><span class="sxs-lookup"><span data-stu-id="94db6-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="94db6-109">無效的 `VARIANT` 範例，包含具有 `VARTYPE` VT_EMPTY &#124; VT_BYREF 的 `VARIANT` 或具有 `VARTYPE` VT_VARIANT 的 `VARIANT`。</span><span class="sxs-lookup"><span data-stu-id="94db6-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="94db6-110">解決方式</span><span class="sxs-lookup"><span data-stu-id="94db6-110">Resolution</span></span>  
 <span data-ttu-id="94db6-111">傳遞 `VARIANT` 的機器碼或 Unmanaged 程式碼必須確保 `VARIANT` 格式正確且已初始化。</span><span class="sxs-lookup"><span data-stu-id="94db6-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="94db6-112">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="94db6-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="94db6-113">此 MDA 對執行階段行為沒有影響。</span><span class="sxs-lookup"><span data-stu-id="94db6-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="94db6-114">Output</span><span class="sxs-lookup"><span data-stu-id="94db6-114">Output</span></span>  
 <span data-ttu-id="94db6-115">MDA 訊息，指出執行階段偵測到無效的 `VARIANT` 由 Unmanaged 模組傳遞至 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="94db6-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="94db6-116">組態</span><span class="sxs-lookup"><span data-stu-id="94db6-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94db6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94db6-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="94db6-118">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="94db6-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="94db6-119">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="94db6-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
