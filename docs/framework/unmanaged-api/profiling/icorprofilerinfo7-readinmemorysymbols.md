---
title: ICorProfilerInfo7::ReadInMemorySymbols
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955365"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="c9fc2-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="c9fc2-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="c9fc2-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="c9fc2-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="c9fc2-104">從記憶體中的符號資料流程讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9fc2-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9fc2-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9fc2-106">參數</span><span class="sxs-lookup"><span data-stu-id="c9fc2-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c9fc2-107">在包含記憶體中資料流程之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="c9fc2-108">在記憶體內部資料流程內要開始讀取位元組的位移。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="c9fc2-109">脫銷要將資料複製到其中之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="c9fc2-110">緩衝區應該有`countSymbolBytes`可用的空間。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="c9fc2-111">在要複製的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="c9fc2-112">脫銷當此方法傳回時, 會包含實際讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9fc2-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9fc2-113">Return Value</span></span>  
 <span data-ttu-id="c9fc2-114">`S_OK`如果讀取非零的位元組數目, 則為。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="c9fc2-115">`CORPROF_E_MODULE_IS_DYNAMIC`, 如果模組是使用<xref:System.Reflection.Emit>建立的, 則為。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9fc2-116">備註</span><span class="sxs-lookup"><span data-stu-id="c9fc2-116">Remarks</span></span>  
 <span data-ttu-id="c9fc2-117">方法會嘗試從記憶體`countSymbolBytes`中資料流程內的位移`symbolsReadOffset`開始讀取資料。 `ReadInMemorySymbols`</span><span class="sxs-lookup"><span data-stu-id="c9fc2-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="c9fc2-118">資料會複製到`pSymbolBytes`, 這應該會有`countSymbolBytes`可用的空間。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="c9fc2-119">`pCountSymbolsBytesRead`包含讀取的實際位元組數目, `countSymbolBytes`如果到達資料流程末端, 則可能小於。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9fc2-120">目前的執行不支援反映。發出。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="c9fc2-121">如果模組是使用反映所建立, 則方法`CORPROF_E_MODULE_IS_DYNAMIC`會傳回。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9fc2-122">需求</span><span class="sxs-lookup"><span data-stu-id="c9fc2-122">Requirements</span></span>  
 <span data-ttu-id="c9fc2-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9fc2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9fc2-124">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="c9fc2-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9fc2-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9fc2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9fc2-126">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9fc2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9fc2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9fc2-127">See also</span></span>

- [<span data-ttu-id="c9fc2-128">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="c9fc2-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
