---
title: "ICorDebugNativeFrame::SetIP 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 25b4f42eb6f10ecade468824d9d790a2bce740a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="6c407-102">ICorDebugNativeFrame::SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="6c407-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="6c407-103">將指定的位移位置的指令指標原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c407-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c407-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c407-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c407-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c407-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="6c407-106">[in]原生程式碼中的位移的位置。</span><span class="sxs-lookup"><span data-stu-id="6c407-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c407-107">備註</span><span class="sxs-lookup"><span data-stu-id="6c407-107">Remarks</span></span>  
 <span data-ttu-id="6c407-108">呼叫`SetIP`立即使所有框架和目前執行緒的鏈結。</span><span class="sxs-lookup"><span data-stu-id="6c407-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="6c407-109">如果偵錯工具需要呼叫之後的畫面格資訊`SetIP`，它必須執行新的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="6c407-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="6c407-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)會嘗試保留的堆疊框架是處於有效狀態。</span><span class="sxs-lookup"><span data-stu-id="6c407-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="6c407-111">不過，即使框架是處於有效狀態，只要執行階段而言，仍可能有問題，例如未初始化的區域變數，等等。</span><span class="sxs-lookup"><span data-stu-id="6c407-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="6c407-112">呼叫端會負責確保執行程式的一致性。</span><span class="sxs-lookup"><span data-stu-id="6c407-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="6c407-113">64 位元平台上，指令指標無法移出`catch`或`finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="6c407-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="6c407-114">如果`SetIP`稱為 「 若要讓這類的 64 位元平台上移動，它會傳回 HRESULT，指出失敗。</span><span class="sxs-lookup"><span data-stu-id="6c407-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c407-115">需求</span><span class="sxs-lookup"><span data-stu-id="6c407-115">Requirements</span></span>  
 <span data-ttu-id="6c407-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c407-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c407-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c407-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c407-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c407-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c407-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c407-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c407-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c407-120">See Also</span></span>  
 
