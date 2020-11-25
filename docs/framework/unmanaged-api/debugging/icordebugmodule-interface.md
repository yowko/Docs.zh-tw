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
ms.openlocfilehash: 86e17b48bc491c45f8b46be23ab626dc1f2a6962
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709839"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="27ba2-102">ICorDebugModule 介面</span><span class="sxs-lookup"><span data-stu-id="27ba2-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="27ba2-103">代表 common language runtime (CLR) 模組，這是可執行檔或動態連結程式庫 (DLL) 。</span><span class="sxs-lookup"><span data-stu-id="27ba2-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27ba2-104">方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-104">Methods</span></span>  
  
|<span data-ttu-id="27ba2-105">方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-105">Method</span></span>|<span data-ttu-id="27ba2-106">描述</span><span class="sxs-lookup"><span data-stu-id="27ba2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27ba2-107">CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-107">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="27ba2-108">未實作。</span><span class="sxs-lookup"><span data-stu-id="27ba2-108">Not implemented.</span></span>|  
|[<span data-ttu-id="27ba2-109">EnableClassLoadCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-109">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="27ba2-110">判斷是否針對此模組呼叫 [ICorDebugManagedCallback：： LoadClass](icordebugmanagedcallback-loadclass-method.md) 和 [ICorDebugManagedCallback：： UnloadClass](icordebugmanagedcallback-unloadclass-method.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="27ba2-110">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="27ba2-111">EnableJITDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-111">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="27ba2-112">判斷及時 (JIT) 編譯器是否保留此模組內方法的偵錯工具資訊。</span><span class="sxs-lookup"><span data-stu-id="27ba2-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="27ba2-113">GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-113">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="27ba2-114">取得此模組的包含元件。</span><span class="sxs-lookup"><span data-stu-id="27ba2-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="27ba2-115">GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-115">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="27ba2-116">取得模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="27ba2-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="27ba2-117">GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-117">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="27ba2-118">從中繼資料取得 ICorDebugClass。</span><span class="sxs-lookup"><span data-stu-id="27ba2-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="27ba2-119">GetEditAndContinueSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-119">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="27ba2-120">已取代。</span><span class="sxs-lookup"><span data-stu-id="27ba2-120">Deprecated.</span></span>|  
|[<span data-ttu-id="27ba2-121">GetFunctionFromRVA 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-121">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="27ba2-122">未實作。</span><span class="sxs-lookup"><span data-stu-id="27ba2-122">Not implemented.</span></span>|  
|[<span data-ttu-id="27ba2-123">GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-123">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="27ba2-124">取得元資料標記所指定的函式。</span><span class="sxs-lookup"><span data-stu-id="27ba2-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="27ba2-125">GetGlobalVariableValue 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-125">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="27ba2-126">取得指定之全域變數的值物件。</span><span class="sxs-lookup"><span data-stu-id="27ba2-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="27ba2-127">GetMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-127">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="27ba2-128">取得中繼資料介面指標，可用來檢查模組的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="27ba2-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="27ba2-129">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-129">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="27ba2-130">取得模組的檔案名。</span><span class="sxs-lookup"><span data-stu-id="27ba2-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="27ba2-131">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-131">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="27ba2-132">取得此模組的包含進程。</span><span class="sxs-lookup"><span data-stu-id="27ba2-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="27ba2-133">GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-133">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="27ba2-134">取得模組的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="27ba2-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="27ba2-135">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-135">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="27ba2-136">取得此模組的資料表專案標記。</span><span class="sxs-lookup"><span data-stu-id="27ba2-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="27ba2-137">IsDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-137">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="27ba2-138">指出模組是否為動態。</span><span class="sxs-lookup"><span data-stu-id="27ba2-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="27ba2-139">IsInMemory 方法</span><span class="sxs-lookup"><span data-stu-id="27ba2-139">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="27ba2-140">指出此模組是否只存在於記憶體中。</span><span class="sxs-lookup"><span data-stu-id="27ba2-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27ba2-141">備註</span><span class="sxs-lookup"><span data-stu-id="27ba2-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27ba2-142">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="27ba2-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27ba2-143">需求</span><span class="sxs-lookup"><span data-stu-id="27ba2-143">Requirements</span></span>  

 <span data-ttu-id="27ba2-144">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27ba2-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27ba2-145">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27ba2-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27ba2-146">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27ba2-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27ba2-147">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27ba2-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ba2-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27ba2-148">See also</span></span>

- [<span data-ttu-id="27ba2-149">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="27ba2-149">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="27ba2-150">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="27ba2-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
