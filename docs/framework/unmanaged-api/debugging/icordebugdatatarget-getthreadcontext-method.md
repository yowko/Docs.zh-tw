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
ms.openlocfilehash: 2db073f6bde3ded27f8e1aa41bfcb87e764745f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174963"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="9102c-102">ICorDebugDataTarget::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="9102c-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="9102c-103">傳回針對指定的執行緒目前的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="9102c-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9102c-104">語法</span><span class="sxs-lookup"><span data-stu-id="9102c-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9102c-105">參數</span><span class="sxs-lookup"><span data-stu-id="9102c-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="9102c-106">[in]要擷取之內容的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="9102c-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="9102c-107">識別碼是由作業系統定義的。</span><span class="sxs-lookup"><span data-stu-id="9102c-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="9102c-108">[in]表示應讀取內容的哪些部分的平台相依旗標的位元組合。</span><span class="sxs-lookup"><span data-stu-id="9102c-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="9102c-109">[in] `pContext` 的大小。</span><span class="sxs-lookup"><span data-stu-id="9102c-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="9102c-110">[out]將儲存執行緒內容緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9102c-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9102c-111">備註</span><span class="sxs-lookup"><span data-stu-id="9102c-111">Remarks</span></span>  
 <span data-ttu-id="9102c-112">在 Windows 平台，`pContext`必須是`CONTEXT`（在 WinNT.h 中定義） 的結構，這是適用於所指定的機器類型[icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="9102c-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> `contextFlags` <span data-ttu-id="9102c-113">必須有相同的值，如同`ContextFlags`欄位`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="9102c-113">must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="9102c-114">`CONTEXT`結構是處理器特定; 請參閱 WinNT.h 檔案，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="9102c-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9102c-115">需求</span><span class="sxs-lookup"><span data-stu-id="9102c-115">Requirements</span></span>  
 <span data-ttu-id="9102c-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9102c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9102c-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9102c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9102c-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9102c-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9102c-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9102c-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9102c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9102c-120">See also</span></span>

- [<span data-ttu-id="9102c-121">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="9102c-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="9102c-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9102c-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9102c-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="9102c-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
