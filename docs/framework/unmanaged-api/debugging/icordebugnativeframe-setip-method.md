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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 604486a074c3dbe3d19b741df28499ee03e1b2e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193274"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="23be9-102">ICorDebugNativeFrame::SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="23be9-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="23be9-103">指令指標設定為原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="23be9-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23be9-104">語法</span><span class="sxs-lookup"><span data-stu-id="23be9-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23be9-105">參數</span><span class="sxs-lookup"><span data-stu-id="23be9-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="23be9-106">[in]原生程式碼中的位移的位置。</span><span class="sxs-lookup"><span data-stu-id="23be9-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23be9-107">備註</span><span class="sxs-lookup"><span data-stu-id="23be9-107">Remarks</span></span>  
 <span data-ttu-id="23be9-108">呼叫`SetIP`立即使其失效，所有的框架和目前執行緒的鏈結。</span><span class="sxs-lookup"><span data-stu-id="23be9-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="23be9-109">如果偵錯工具必須在呼叫之後的畫面格資訊`SetIP`，它必須執行新的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="23be9-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="23be9-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)會嘗試將保留的堆疊框架處於有效狀態。</span><span class="sxs-lookup"><span data-stu-id="23be9-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="23be9-111">不過，即使框架是處於有效狀態，只要執行階段而言，仍可能有問題，例如未初始化的本機變數，依此類推。</span><span class="sxs-lookup"><span data-stu-id="23be9-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="23be9-112">呼叫端必須負責確保執行程式的一致性。</span><span class="sxs-lookup"><span data-stu-id="23be9-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="23be9-113">在 64 位元平台，指令指標無法移出`catch`或`finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="23be9-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="23be9-114">如果`SetIP`呼叫進行的 64 位元平台上的這類移動，它會傳回 HRESULT，指出失敗。</span><span class="sxs-lookup"><span data-stu-id="23be9-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23be9-115">需求</span><span class="sxs-lookup"><span data-stu-id="23be9-115">Requirements</span></span>  
 <span data-ttu-id="23be9-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23be9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23be9-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23be9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23be9-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23be9-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="23be9-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="23be9-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="23be9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23be9-120">See also</span></span>
