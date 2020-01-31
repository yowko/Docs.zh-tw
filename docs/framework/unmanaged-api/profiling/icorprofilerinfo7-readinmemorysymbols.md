---
title: ICorProfilerInfo7：： ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: 53c01d2db44f4d0adf1ba5b9cc225ab49581aa5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868339"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="fc67b-102">ICorProfilerInfo7：： ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="fc67b-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="fc67b-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="fc67b-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="fc67b-104">從記憶體中的符號資料流程讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="fc67b-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc67b-105">語法</span><span class="sxs-lookup"><span data-stu-id="fc67b-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc67b-106">參數</span><span class="sxs-lookup"><span data-stu-id="fc67b-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="fc67b-107">在包含記憶體中資料流程之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fc67b-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="fc67b-108">在記憶體內部資料流程內要開始讀取位元組的位移。</span><span class="sxs-lookup"><span data-stu-id="fc67b-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="fc67b-109">脫銷要將資料複製到其中之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="fc67b-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="fc67b-110">緩衝區應具有可用的空間 `countSymbolBytes`。</span><span class="sxs-lookup"><span data-stu-id="fc67b-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="fc67b-111">在要複製的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="fc67b-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="fc67b-112">脫銷當此方法傳回時，會包含實際讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="fc67b-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc67b-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="fc67b-113">Return Value</span></span>  
 <span data-ttu-id="fc67b-114">`S_OK`，如果讀取的是非零的位元組數目，則為。</span><span class="sxs-lookup"><span data-stu-id="fc67b-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="fc67b-115">`CORPROF_E_MODULE_IS_DYNAMIC`，如果模組是使用 <xref:System.Reflection.Emit>所建立的。</span><span class="sxs-lookup"><span data-stu-id="fc67b-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc67b-116">備註</span><span class="sxs-lookup"><span data-stu-id="fc67b-116">Remarks</span></span>  
 <span data-ttu-id="fc67b-117">`ReadInMemorySymbols` 方法會嘗試讀取記憶體中資料流程內從 offset `symbolsReadOffset` 開始的 `countSymbolBytes` 資料。</span><span class="sxs-lookup"><span data-stu-id="fc67b-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="fc67b-118">資料會複製到 `pSymbolBytes`，這應該會有 `countSymbolBytes` 的可用空間。</span><span class="sxs-lookup"><span data-stu-id="fc67b-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="fc67b-119">`pCountSymbolsBytesRead` 包含讀取的實際位元組數目，如果到達資料流程末端，則可能小於 `countSymbolBytes`。</span><span class="sxs-lookup"><span data-stu-id="fc67b-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc67b-120">目前的執行不支援反映。發出。</span><span class="sxs-lookup"><span data-stu-id="fc67b-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="fc67b-121">如果模組是使用反映所建立，則方法會傳回 `CORPROF_E_MODULE_IS_DYNAMIC`。</span><span class="sxs-lookup"><span data-stu-id="fc67b-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc67b-122">需求</span><span class="sxs-lookup"><span data-stu-id="fc67b-122">Requirements</span></span>  
 <span data-ttu-id="fc67b-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc67b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc67b-124">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc67b-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc67b-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc67b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc67b-126">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc67b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc67b-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc67b-127">See also</span></span>

- [<span data-ttu-id="fc67b-128">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="fc67b-128">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
