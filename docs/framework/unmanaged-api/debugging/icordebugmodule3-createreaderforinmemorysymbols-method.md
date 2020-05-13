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
ms.openlocfilehash: 2a8200f942405395429db182b7501a07fc1f930a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212317"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="81f1d-102">ICorDebugModule3::CreateReaderForInMemorySymbols 方法</span><span class="sxs-lookup"><span data-stu-id="81f1d-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="81f1d-103">建立動態模組的偵錯工具符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="81f1d-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="81f1d-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="81f1d-105">參數</span><span class="sxs-lookup"><span data-stu-id="81f1d-105">Parameters</span></span>  
 <span data-ttu-id="81f1d-106">riid</span><span class="sxs-lookup"><span data-stu-id="81f1d-106">riid</span></span>  
 <span data-ttu-id="81f1d-107">在要傳回之 COM 介面的 IID。</span><span class="sxs-lookup"><span data-stu-id="81f1d-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="81f1d-108">一般來說，這是[ISymUnmanagedReader 介面](../diagnostics/isymunmanagedreader-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="81f1d-108">Typically, this is an [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="81f1d-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="81f1d-109">ppObj</span></span>  
 <span data-ttu-id="81f1d-110">脫銷傳回之介面指標的指標。</span><span class="sxs-lookup"><span data-stu-id="81f1d-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81f1d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="81f1d-111">Return Value</span></span>  
 <span data-ttu-id="81f1d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="81f1d-112">S_OK</span></span>  
 <span data-ttu-id="81f1d-113">已成功建立讀取器。</span><span class="sxs-lookup"><span data-stu-id="81f1d-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="81f1d-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="81f1d-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="81f1d-115">模組不是記憶體內部或動態模組。</span><span class="sxs-lookup"><span data-stu-id="81f1d-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="81f1d-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81f1d-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="81f1d-117">符號尚未由應用程式提供或尚未使用。</span><span class="sxs-lookup"><span data-stu-id="81f1d-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="81f1d-118">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="81f1d-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="81f1d-119">無法建立讀取器。</span><span class="sxs-lookup"><span data-stu-id="81f1d-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81f1d-120">備註</span><span class="sxs-lookup"><span data-stu-id="81f1d-120">Remarks</span></span>  
 <span data-ttu-id="81f1d-121">這個方法也可以用來建立記憶體內部（非動態）模組的符號讀取器物件，但只能在第一次使用符號之後（以[UpdateModuleSymbols 方法](icordebugmanagedcallback-updatemodulesymbols-method.md)回呼表示）。</span><span class="sxs-lookup"><span data-stu-id="81f1d-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="81f1d-122">這個方法會在每次呼叫時傳回新的讀取器實例（例如[CComPtrBase：： CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)）。</span><span class="sxs-lookup"><span data-stu-id="81f1d-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="81f1d-123">因此，只有在基礎資料可能已變更（亦即，收到[LoadClass 方法](icordebugmanagedcallback-loadclass-method.md)回呼時）時，偵錯工具才應該快取結果，並要求新的實例。</span><span class="sxs-lookup"><span data-stu-id="81f1d-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="81f1d-124">動態模組在載入第一個類型（如[LoadClass 方法](icordebugmanagedcallback-loadclass-method.md)回呼所指示）之前，不會有任何可用的符號。</span><span class="sxs-lookup"><span data-stu-id="81f1d-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81f1d-125">需求</span><span class="sxs-lookup"><span data-stu-id="81f1d-125">Requirements</span></span>  
 <span data-ttu-id="81f1d-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81f1d-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81f1d-127">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81f1d-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81f1d-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81f1d-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81f1d-129">**.NET Framework 版本：** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="81f1d-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f1d-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="81f1d-130">See also</span></span>

- [<span data-ttu-id="81f1d-131">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="81f1d-131">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="81f1d-132">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="81f1d-132">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="81f1d-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="81f1d-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
