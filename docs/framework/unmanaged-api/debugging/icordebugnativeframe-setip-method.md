---
title: ICorDebugNativeFrame::SetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 1d978cab0817af68356d95d635f8d2bfa3fd546a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096745"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="bf2c5-102">ICorDebugNativeFrame::SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="bf2c5-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="bf2c5-103">將指令指標設定為原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf2c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="bf2c5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf2c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="bf2c5-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="bf2c5-106">在機器碼中的位移位置。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf2c5-107">備註</span><span class="sxs-lookup"><span data-stu-id="bf2c5-107">Remarks</span></span>  
 <span data-ttu-id="bf2c5-108">`SetIP` 的呼叫會立即使目前線程的所有框架和鏈失效。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="bf2c5-109">如果偵錯工具在呼叫 `SetIP`之後需要框架資訊，則必須執行新的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="bf2c5-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)會嘗試將堆疊框架保持在有效的狀態。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="bf2c5-111">不過，即使畫面格處於有效的狀態，只要執行時間關心，仍然可能會有問題，例如未初始化的區域變數等等。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="bf2c5-112">呼叫端負責確保執行中程式的一致性。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="bf2c5-113">在64位平臺上，無法將指令指標移出 `catch` 或 `finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="bf2c5-114">如果呼叫 `SetIP` 以在64位平臺上進行這類移動，則會傳回表示失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf2c5-115">需求</span><span class="sxs-lookup"><span data-stu-id="bf2c5-115">Requirements</span></span>  
 <span data-ttu-id="bf2c5-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bf2c5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf2c5-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf2c5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf2c5-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf2c5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf2c5-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf2c5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf2c5-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf2c5-120">See also</span></span>
