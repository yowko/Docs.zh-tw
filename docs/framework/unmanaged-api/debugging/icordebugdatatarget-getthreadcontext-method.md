---
title: ICorDebugDataTarget::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0d579ffe6bf0722365e789ba3a43ce1dce06fac
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502991"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="2b53a-102">ICorDebugDataTarget::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="2b53a-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="2b53a-103">傳回針對指定的執行緒目前的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="2b53a-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b53a-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b53a-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b53a-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b53a-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="2b53a-106">[in]要擷取之內容的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="2b53a-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="2b53a-107">識別碼是由作業系統定義的。</span><span class="sxs-lookup"><span data-stu-id="2b53a-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="2b53a-108">[in]表示應讀取內容的哪些部分的平台相依旗標的位元組合。</span><span class="sxs-lookup"><span data-stu-id="2b53a-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2b53a-109">[in] `pContext` 的大小。</span><span class="sxs-lookup"><span data-stu-id="2b53a-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="2b53a-110">[out]將儲存執行緒內容緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2b53a-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b53a-111">備註</span><span class="sxs-lookup"><span data-stu-id="2b53a-111">Remarks</span></span>  
 <span data-ttu-id="2b53a-112">在 Windows 平台，`pContext`必須是`CONTEXT`（在 WinNT.h 中定義） 的結構，這是適用於所指定的機器類型[icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2b53a-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="2b53a-113">`contextFlags` 必須有相同的值，如同`ContextFlags`欄位`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="2b53a-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="2b53a-114">`CONTEXT`結構是處理器特定; 請參閱 WinNT.h 檔案，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2b53a-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b53a-115">需求</span><span class="sxs-lookup"><span data-stu-id="2b53a-115">Requirements</span></span>  
 <span data-ttu-id="2b53a-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b53a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b53a-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b53a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b53a-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b53a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b53a-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b53a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b53a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b53a-120">See also</span></span>
- [<span data-ttu-id="2b53a-121">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="2b53a-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="2b53a-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2b53a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2b53a-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="2b53a-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
