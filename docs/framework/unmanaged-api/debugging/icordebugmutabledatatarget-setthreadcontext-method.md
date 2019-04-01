---
title: ICorDebugMutableDataTarget::SetThreadContext 方法
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbbe4dcec29ba85c64b6e22a4348c56e80daf623
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479182"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="94ee2-102">ICorDebugMutableDataTarget::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="94ee2-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="94ee2-103">設定執行緒的內容 (登錄值)。</span><span class="sxs-lookup"><span data-stu-id="94ee2-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ee2-104">語法</span><span class="sxs-lookup"><span data-stu-id="94ee2-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94ee2-105">參數</span><span class="sxs-lookup"><span data-stu-id="94ee2-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="94ee2-106">[in] 作業系統定義的執行緒識別項。</span><span class="sxs-lookup"><span data-stu-id="94ee2-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="94ee2-107">[in] 所要寫入的 `pContext` 緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="94ee2-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="94ee2-108">[in] 所要寫入的位元組指標。</span><span class="sxs-lookup"><span data-stu-id="94ee2-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94ee2-109">備註</span><span class="sxs-lookup"><span data-stu-id="94ee2-109">Remarks</span></span>  
 <span data-ttu-id="94ee2-110">`SetThreadContext` 方法會針對作業系統定義之 `dwThreadID` 引數所指定的執行緒，更新目前的內容。</span><span class="sxs-lookup"><span data-stu-id="94ee2-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="94ee2-111">內容記錄的格式取決於所指定的平台[icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="94ee2-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="94ee2-112">在 Windows，這是[內容](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context)結構。</span><span class="sxs-lookup"><span data-stu-id="94ee2-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94ee2-113">需求</span><span class="sxs-lookup"><span data-stu-id="94ee2-113">Requirements</span></span>  
 <span data-ttu-id="94ee2-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94ee2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94ee2-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94ee2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94ee2-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94ee2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94ee2-117">**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94ee2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ee2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94ee2-118">See also</span></span>
- [<span data-ttu-id="94ee2-119">ICorDebugMutableDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="94ee2-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="94ee2-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="94ee2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
