---
title: ICorDebugModule3::CreateReaderForInMemorySymbols 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 342739f6c71e9c576e557433dc6abd0adbf38c8c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468348"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="77740-102">ICorDebugModule3::CreateReaderForInMemorySymbols 方法</span><span class="sxs-lookup"><span data-stu-id="77740-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="77740-103">建立動態模組的偵錯符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="77740-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77740-104">語法</span><span class="sxs-lookup"><span data-stu-id="77740-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77740-105">參數</span><span class="sxs-lookup"><span data-stu-id="77740-105">Parameters</span></span>  
 <span data-ttu-id="77740-106">riid</span><span class="sxs-lookup"><span data-stu-id="77740-106">riid</span></span>  
 <span data-ttu-id="77740-107">[in]要傳回的 COM 介面的 IID。</span><span class="sxs-lookup"><span data-stu-id="77740-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="77740-108">一般而言，這是[ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="77740-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="77740-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="77740-109">ppObj</span></span>  
 <span data-ttu-id="77740-110">[out]傳回的介面指標的指標。</span><span class="sxs-lookup"><span data-stu-id="77740-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77740-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="77740-111">Return Value</span></span>  
 <span data-ttu-id="77740-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="77740-112">S_OK</span></span>  
 <span data-ttu-id="77740-113">已成功建立讀取器。</span><span class="sxs-lookup"><span data-stu-id="77740-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="77740-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="77740-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="77740-115">此模組不是記憶體中或動態模組。</span><span class="sxs-lookup"><span data-stu-id="77740-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="77740-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77740-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="77740-117">符號尚未提供應用程式，或尚無法使用。</span><span class="sxs-lookup"><span data-stu-id="77740-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="77740-118">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="77740-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="77740-119">無法建立讀取器。</span><span class="sxs-lookup"><span data-stu-id="77740-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77740-120">備註</span><span class="sxs-lookup"><span data-stu-id="77740-120">Remarks</span></span>  
 <span data-ttu-id="77740-121">這個方法也可以用來建立記憶體中 （非動態） 模組的符號讀取器物件，但只有第一次符號之後 (由[UpdateModuleSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)回呼)。</span><span class="sxs-lookup"><span data-stu-id="77740-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="77740-122">每次呼叫時，這個方法會傳回新的讀取器執行個體 (例如[CComPtrBase::CoCreateInstance](https://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6))。</span><span class="sxs-lookup"><span data-stu-id="77740-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](https://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span></span> <span data-ttu-id="77740-123">因此，偵錯工具應該快取結果，並要求新的執行個體，可能會變更基礎資料時才 (亦即，當[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)接收回呼)。</span><span class="sxs-lookup"><span data-stu-id="77740-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="77740-124">動態模組沒有任何可用的符號之前已載入的第一個類型 (如所示[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)回呼)。</span><span class="sxs-lookup"><span data-stu-id="77740-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77740-125">需求</span><span class="sxs-lookup"><span data-stu-id="77740-125">Requirements</span></span>  
 <span data-ttu-id="77740-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77740-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77740-127">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77740-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77740-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77740-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77740-129">**.NET framework 版本：** 4.5，4，3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="77740-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77740-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77740-130">See Also</span></span>  
 [<span data-ttu-id="77740-131">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="77740-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="77740-132">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="77740-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="77740-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="77740-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
