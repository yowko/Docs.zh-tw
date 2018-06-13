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
ms.openlocfilehash: ab2fbf6bb08a33158ea450f0f19eca50e280d8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412876"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="ba694-102">ICorDebugDataTarget::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="ba694-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="ba694-103">傳回指定的執行緒目前的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="ba694-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba694-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba694-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba694-105">參數</span><span class="sxs-lookup"><span data-stu-id="ba694-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="ba694-106">[in]要擷取之內容的執行緒識別項。</span><span class="sxs-lookup"><span data-stu-id="ba694-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="ba694-107">作業系統所定義的識別項。</span><span class="sxs-lookup"><span data-stu-id="ba694-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="ba694-108">[in]平台相關旗標，表示內容的哪些部分應該讀取的位元組合。</span><span class="sxs-lookup"><span data-stu-id="ba694-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="ba694-109">[in] `pContext` 的大小。</span><span class="sxs-lookup"><span data-stu-id="ba694-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="ba694-110">[out]要儲存的執行緒內容緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ba694-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba694-111">備註</span><span class="sxs-lookup"><span data-stu-id="ba694-111">Remarks</span></span>  
 <span data-ttu-id="ba694-112">Windows 平台上，`pContext`必須`CONTEXT`結構 （在 WinNT.h 中定義），這是適用於所指定的電腦類型[icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ba694-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="ba694-113">`contextFlags` 必須有相同的值，如同`ContextFlags`欄位`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="ba694-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="ba694-114">`CONTEXT`結構處理器特定; 請參閱 WinNT.h 檔以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ba694-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba694-115">需求</span><span class="sxs-lookup"><span data-stu-id="ba694-115">Requirements</span></span>  
 <span data-ttu-id="ba694-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba694-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba694-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba694-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba694-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba694-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba694-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba694-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba694-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba694-120">See Also</span></span>  
 [<span data-ttu-id="ba694-121">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="ba694-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="ba694-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ba694-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ba694-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="ba694-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
