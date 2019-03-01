---
title: ICorDebugModule 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fd8314c018653703a262c8c43e6113886c25047
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978679"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="a5ed9-102">ICorDebugModule 介面</span><span class="sxs-lookup"><span data-stu-id="a5ed9-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="a5ed9-103">表示 common language runtime (CLR) 模組，可執行檔或動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5ed9-104">方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-104">Methods</span></span>  
  
|<span data-ttu-id="a5ed9-105">方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-105">Method</span></span>|<span data-ttu-id="a5ed9-106">描述</span><span class="sxs-lookup"><span data-stu-id="a5ed9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5ed9-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="a5ed9-108">未實作。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-108">Not implemented.</span></span>|  
|[<span data-ttu-id="a5ed9-109">EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="a5ed9-110">決定是否[icordebugmanagedcallback:: Loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)並[icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回呼會呼叫此模組。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="a5ed9-111">EnableJITDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="a5ed9-112">決定是否在 just-in-time (JIT) 編譯器會保留在這個模組中方法的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="a5ed9-113">GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="a5ed9-114">取得此模組包含組件。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="a5ed9-115">GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="a5ed9-116">取得模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="a5ed9-117">GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="a5ed9-118">取得 ICorDebugClass 從中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="a5ed9-119">GetEditAndContinueSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="a5ed9-120">已取代。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-120">Deprecated.</span></span>|  
|[<span data-ttu-id="a5ed9-121">GetFunctionFromRVA 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="a5ed9-122">未實作。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-122">Not implemented.</span></span>|  
|[<span data-ttu-id="a5ed9-123">GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="a5ed9-124">取得指定中繼資料語彙基元的函式。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="a5ed9-125">GetGlobalVariableValue 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="a5ed9-126">取得指定之全域變數的值物件。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="a5ed9-127">GetMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="a5ed9-128">取得可用來檢查模組的中繼資料的中繼資料介面指標。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="a5ed9-129">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="a5ed9-130">取得模組的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="a5ed9-131">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="a5ed9-132">取得此模組包含的程序。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="a5ed9-133">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="a5ed9-134">取得模組的大小，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="a5ed9-135">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="a5ed9-136">取得資料表項目，此模組的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="a5ed9-137">IsDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="a5ed9-138">指出模組是否為動態。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="a5ed9-139">IsInMemory 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed9-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="a5ed9-140">指出是否此模組只存在於記憶體。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5ed9-141">備註</span><span class="sxs-lookup"><span data-stu-id="a5ed9-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5ed9-142">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5ed9-143">需求</span><span class="sxs-lookup"><span data-stu-id="a5ed9-143">Requirements</span></span>  
 <span data-ttu-id="a5ed9-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5ed9-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5ed9-145">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5ed9-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5ed9-146">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5ed9-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5ed9-147">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5ed9-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ed9-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5ed9-148">See also</span></span>
- [<span data-ttu-id="a5ed9-149">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="a5ed9-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="a5ed9-150">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a5ed9-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
