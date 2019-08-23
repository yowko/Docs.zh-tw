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
ms.openlocfilehash: 5dce4f5859568c1288610e171286a5919dc8b19b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962435"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="07301-102">ICorDebugModule 介面</span><span class="sxs-lookup"><span data-stu-id="07301-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="07301-103">表示 common language runtime (CLR) 模組, 這是可執行檔或動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="07301-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07301-104">方法</span><span class="sxs-lookup"><span data-stu-id="07301-104">Methods</span></span>  
  
|<span data-ttu-id="07301-105">方法</span><span class="sxs-lookup"><span data-stu-id="07301-105">Method</span></span>|<span data-ttu-id="07301-106">描述</span><span class="sxs-lookup"><span data-stu-id="07301-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07301-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="07301-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="07301-108">未實作。</span><span class="sxs-lookup"><span data-stu-id="07301-108">Not implemented.</span></span>|  
|[<span data-ttu-id="07301-109">EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="07301-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="07301-110">判斷是否針對此模組呼叫[ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)和[ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="07301-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="07301-111">EnableJITDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="07301-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="07301-112">判斷即時 (JIT) 編譯器是否保留此模組中之方法的偵錯工具資訊。</span><span class="sxs-lookup"><span data-stu-id="07301-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="07301-113">GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="07301-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="07301-114">取得此模組的包含元件。</span><span class="sxs-lookup"><span data-stu-id="07301-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="07301-115">GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="07301-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="07301-116">取得模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="07301-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="07301-117">GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="07301-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="07301-118">從中繼資料取得 ICorDebugClass。</span><span class="sxs-lookup"><span data-stu-id="07301-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="07301-119">GetEditAndContinueSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="07301-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="07301-120">已取代。</span><span class="sxs-lookup"><span data-stu-id="07301-120">Deprecated.</span></span>|  
|[<span data-ttu-id="07301-121">GetFunctionFromRVA 方法</span><span class="sxs-lookup"><span data-stu-id="07301-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="07301-122">未實作。</span><span class="sxs-lookup"><span data-stu-id="07301-122">Not implemented.</span></span>|  
|[<span data-ttu-id="07301-123">GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="07301-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="07301-124">取得元資料標記所指定的函式。</span><span class="sxs-lookup"><span data-stu-id="07301-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="07301-125">GetGlobalVariableValue 方法</span><span class="sxs-lookup"><span data-stu-id="07301-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="07301-126">取得指定之全域變數的值物件。</span><span class="sxs-lookup"><span data-stu-id="07301-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="07301-127">GetMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="07301-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="07301-128">取得中繼資料介面指標, 可用於檢查模組的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="07301-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="07301-129">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="07301-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="07301-130">取得模組的檔案名。</span><span class="sxs-lookup"><span data-stu-id="07301-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="07301-131">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="07301-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="07301-132">取得此模組的包含進程。</span><span class="sxs-lookup"><span data-stu-id="07301-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="07301-133">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="07301-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="07301-134">取得模組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="07301-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="07301-135">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="07301-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="07301-136">取得此模組之資料表專案的 token。</span><span class="sxs-lookup"><span data-stu-id="07301-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="07301-137">IsDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="07301-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="07301-138">指出模組是否為動態。</span><span class="sxs-lookup"><span data-stu-id="07301-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="07301-139">IsInMemory 方法</span><span class="sxs-lookup"><span data-stu-id="07301-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="07301-140">指出此模組是否只存在於記憶體中。</span><span class="sxs-lookup"><span data-stu-id="07301-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07301-141">備註</span><span class="sxs-lookup"><span data-stu-id="07301-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07301-142">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="07301-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07301-143">需求</span><span class="sxs-lookup"><span data-stu-id="07301-143">Requirements</span></span>  
 <span data-ttu-id="07301-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07301-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07301-145">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07301-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07301-146">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07301-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07301-147">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07301-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07301-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07301-148">See also</span></span>

- [<span data-ttu-id="07301-149">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="07301-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="07301-150">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="07301-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
