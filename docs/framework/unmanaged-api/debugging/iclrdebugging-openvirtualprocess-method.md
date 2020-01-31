---
title: ICLRDebugging::OpenVirtualProcess 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: 585b3d605d0df9169c12ca10198846ec0a7fe6d4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793616"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="46e30-102">ICLRDebugging::OpenVirtualProcess 方法</span><span class="sxs-lookup"><span data-stu-id="46e30-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="46e30-103">取得對應至在進程中載入之 common language runtime （CLR）模組的 ICorDebugProcess 介面。</span><span class="sxs-lookup"><span data-stu-id="46e30-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46e30-104">語法</span><span class="sxs-lookup"><span data-stu-id="46e30-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="46e30-105">參數</span><span class="sxs-lookup"><span data-stu-id="46e30-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="46e30-106">在目標進程中模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="46e30-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="46e30-107">如果指定的模組不是 CLR 模組，則會傳回 COR_E_NOT_CLR。</span><span class="sxs-lookup"><span data-stu-id="46e30-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="46e30-108">在資料目標抽象，可讓 managed 偵錯工具檢查進程狀態。</span><span class="sxs-lookup"><span data-stu-id="46e30-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="46e30-109">偵錯工具必須執行[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="46e30-109">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="46e30-110">您應該執行[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)介面，以支援正在進行調試的 CLR 不會安裝在本機電腦上的案例。</span><span class="sxs-lookup"><span data-stu-id="46e30-110">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="46e30-111">在程式庫提供者回呼介面，允許視需要尋找和載入版本特定的偵錯工具程式庫。</span><span class="sxs-lookup"><span data-stu-id="46e30-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="46e30-112">只有當 `ppProcess` 或 `pFlags` 不 `null`時，才需要此參數。</span><span class="sxs-lookup"><span data-stu-id="46e30-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="46e30-113">在此偵錯工具可以 debug 的最高 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="46e30-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="46e30-114">您應該從這個偵錯工具支援的最新 CLR 版本指定主要、次要和組建版本，並將修訂編號設定為65535，以配合未來的就地 CLR 服務版本。</span><span class="sxs-lookup"><span data-stu-id="46e30-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="46e30-115">在要取出的 ICorDebugProcess 介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="46e30-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="46e30-116">目前，唯一接受的值是 IID_CORDEBUGPROCESS3、IID_CORDEBUGPROCESS2 和 IID_CORDEBUGPROCESS。</span><span class="sxs-lookup"><span data-stu-id="46e30-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="46e30-117">脫銷`riidProcess`所識別之 COM 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="46e30-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="46e30-118">[in、out]CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="46e30-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="46e30-119">在輸入時，這個值可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="46e30-119">On input, this value can be `null`.</span></span> <span data-ttu-id="46e30-120">它也可以指向[CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md)結構，在此情況下，結構的 `wStructVersion` 欄位必須初始化為0（零）。</span><span class="sxs-lookup"><span data-stu-id="46e30-120">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="46e30-121">輸出時，傳回的 `CLR_DEBUGGING_VERSION` 結構會填入 CLR 的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="46e30-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="46e30-122">脫銷有關指定執行時間的資訊旗標。</span><span class="sxs-lookup"><span data-stu-id="46e30-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="46e30-123">如需旗標的描述，請參閱[CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md)主題。</span><span class="sxs-lookup"><span data-stu-id="46e30-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46e30-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="46e30-124">Return Value</span></span>  
 <span data-ttu-id="46e30-125">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="46e30-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="46e30-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46e30-126">HRESULT</span></span>|<span data-ttu-id="46e30-127">描述</span><span class="sxs-lookup"><span data-stu-id="46e30-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46e30-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="46e30-128">S_OK</span></span>|<span data-ttu-id="46e30-129">此方法已順利完成。</span><span class="sxs-lookup"><span data-stu-id="46e30-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="46e30-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="46e30-130">E_POINTER</span></span>|<span data-ttu-id="46e30-131">`pDataTarget` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="46e30-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="46e30-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="46e30-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="46e30-133">[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)回呼會傳回錯誤，或未提供有效的控制碼。</span><span class="sxs-lookup"><span data-stu-id="46e30-133">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="46e30-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="46e30-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="46e30-135">`pDataTarget` 不會針對這個版本的執行時間，執行必要的資料目標介面。</span><span class="sxs-lookup"><span data-stu-id="46e30-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="46e30-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="46e30-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="46e30-137">指出的模組不是 CLR 模組。</span><span class="sxs-lookup"><span data-stu-id="46e30-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="46e30-138">當無法偵測到 CLR 模組，因為記憶體已損毀、模組無法使用，或 CLR 版本晚于填充碼版本時，也會傳回此 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="46e30-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="46e30-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="46e30-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="46e30-140">這個執行階段版本不支援此調試模型。</span><span class="sxs-lookup"><span data-stu-id="46e30-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="46e30-141">目前，CLR 版本不支援在 .NET Framework 4 之前的偵錯工具模型。</span><span class="sxs-lookup"><span data-stu-id="46e30-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="46e30-142">在此錯誤之後，`pwszVersion` 輸出參數仍然設定為正確的值。</span><span class="sxs-lookup"><span data-stu-id="46e30-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="46e30-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="46e30-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="46e30-144">CLR 的版本大於此偵錯工具所宣告支援的版本。</span><span class="sxs-lookup"><span data-stu-id="46e30-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="46e30-145">在此錯誤之後，`pwszVersion` 輸出參數仍然設定為正確的值。</span><span class="sxs-lookup"><span data-stu-id="46e30-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="46e30-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="46e30-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="46e30-147">`riidProcess` 介面無法使用。</span><span class="sxs-lookup"><span data-stu-id="46e30-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="46e30-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="46e30-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="46e30-149">`CLR_DEBUGGING_VERSION` 結構沒有可辨識的 `wStructVersion`值。</span><span class="sxs-lookup"><span data-stu-id="46e30-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="46e30-150">目前唯一接受的值是0。</span><span class="sxs-lookup"><span data-stu-id="46e30-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="46e30-151">例外狀況</span><span class="sxs-lookup"><span data-stu-id="46e30-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46e30-152">備註</span><span class="sxs-lookup"><span data-stu-id="46e30-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46e30-153">需求</span><span class="sxs-lookup"><span data-stu-id="46e30-153">Requirements</span></span>  
 <span data-ttu-id="46e30-154">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46e30-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46e30-155">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46e30-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46e30-156">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46e30-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46e30-157">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46e30-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46e30-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="46e30-158">See also</span></span>

- [<span data-ttu-id="46e30-159">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="46e30-159">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="46e30-160">偵錯</span><span class="sxs-lookup"><span data-stu-id="46e30-160">Debugging</span></span>](index.md)
