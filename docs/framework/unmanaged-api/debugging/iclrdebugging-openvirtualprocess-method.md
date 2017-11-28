---
title: "ICLRDebugging::OpenVirtualProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging.OpenVirtualProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a59d676e358b2e06ac04bdf586d8ad416445337
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="b7b0c-102">ICLRDebugging::OpenVirtualProcess 方法</span><span class="sxs-lookup"><span data-stu-id="b7b0c-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="b7b0c-103">取得對應至 common language runtime (CLR) 模組載入處理序中的 ICorDebugProcess 介面。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7b0c-104">Syntax</span></span>  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7b0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7b0c-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="b7b0c-106">[in]目標處理序模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="b7b0c-107">如果指定的模組不是 CLR 模組，將會傳回 COR_E_NOT_CLR。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="b7b0c-108">[in]資料目標抽象概念，可讓 managed 偵錯工具若要檢查處理狀態。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="b7b0c-109">偵錯工具必須實作[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="b7b0c-110">您應該實作[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面，以支援案例所偵錯 CLR 未安裝在本機電腦。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="b7b0c-111">[in]程式庫提供者回呼介面，可讓特定版本的偵錯程式庫找到並載入需求。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="b7b0c-112">這個參數是必要項，只有當`ppProcess`或`pFlags`不`null`。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="b7b0c-113">[in]這個偵錯工具可以偵錯 CLR 最高的版本。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="b7b0c-114">您應該指定主要、 次要、 和建置版本的最新的 CLR 版本，此偵錯工具支援，並設 65535 適應未來就地 CLR 服務版本的修訂編號。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="b7b0c-115">[in]要擷取 ICorDebugProcess 介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="b7b0c-116">目前，唯一接受的值已設定 IID_CORDEBUGPROCESS3、 IID_CORDEBUGPROCESS2 和 IID_CORDEBUGPROCESS。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="b7b0c-117">[out]所識別的 COM 介面指標`riidProcess`。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="b7b0c-118">[in、 out]CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="b7b0c-119">輸入時，這個值可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-119">On input, this value can be `null`.</span></span> <span data-ttu-id="b7b0c-120">它也能指向[CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)結構，在此情況下的結構`wStructVersion`欄位必須初始化為 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="b7b0c-121">在輸出時，傳回`CLR_DEBUGGING_VERSION`結構將會填入 CLR 的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="b7b0c-122">[out]指定的執行階段的相關資訊的旗標。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="b7b0c-123">請參閱[CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)旗標的說明主題。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7b0c-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="b7b0c-124">Return Value</span></span>  
 <span data-ttu-id="b7b0c-125">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b7b0c-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7b0c-126">HRESULT</span></span>|<span data-ttu-id="b7b0c-127">描述</span><span class="sxs-lookup"><span data-stu-id="b7b0c-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7b0c-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7b0c-128">S_OK</span></span>|<span data-ttu-id="b7b0c-129">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="b7b0c-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b7b0c-130">E_POINTER</span></span>|<span data-ttu-id="b7b0c-131">`pDataTarget` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="b7b0c-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="b7b0c-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="b7b0c-133">[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)回呼傳回錯誤，或未提供有效的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="b7b0c-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="b7b0c-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="b7b0c-135">`pDataTarget`未實作必要的資料目標介面，這個版本的執行階段。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="b7b0c-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="b7b0c-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="b7b0c-137">指定的模組不是 CLR 模組。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="b7b0c-138">無法偵測到 CLR 模組，因為記憶體已損毀、 模組就無法使用，或是 CLR 版本晚於填充碼版本時，也會傳回這個 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="b7b0c-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="b7b0c-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="b7b0c-140">這個執行階段版本不支援這個偵錯模型。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="b7b0c-141">目前的偵錯模型不支援的 CLR 版本之前[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-141">Currently, the debugging model is not supported by CLR versions before the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="b7b0c-142">`pwszVersion`輸出參數仍然設定為正確的值之後這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="b7b0c-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="b7b0c-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="b7b0c-144">CLR 版本大於這個偵錯工具會宣告為支援的版本。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="b7b0c-145">`pwszVersion`輸出參數仍然設定為正確的值之後這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="b7b0c-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="b7b0c-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="b7b0c-147">`riidProcess`不提供介面。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="b7b0c-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="b7b0c-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="b7b0c-149">`CLR_DEBUGGING_VERSION`結構沒有可辨識的值`wStructVersion`。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="b7b0c-150">此時唯一接受的值為 0。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b7b0c-151">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b7b0c-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7b0c-152">備註</span><span class="sxs-lookup"><span data-stu-id="b7b0c-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7b0c-153">需求</span><span class="sxs-lookup"><span data-stu-id="b7b0c-153">Requirements</span></span>  
 <span data-ttu-id="b7b0c-154">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7b0c-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b0c-155">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7b0c-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7b0c-156">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7b0c-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7b0c-157">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b0c-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b0c-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7b0c-158">See Also</span></span>  
 [<span data-ttu-id="b7b0c-159">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b7b0c-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b7b0c-160">偵錯</span><span class="sxs-lookup"><span data-stu-id="b7b0c-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
