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
ms.openlocfilehash: c3df5324e23ebeded38f3aa9843f81701f7fd333
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251053"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="51961-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="51961-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="51961-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="51961-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="51961-104">從記憶體中的符號資料流讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="51961-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51961-105">語法</span><span class="sxs-lookup"><span data-stu-id="51961-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51961-106">參數</span><span class="sxs-lookup"><span data-stu-id="51961-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="51961-107">[in]包含記憶體中資料流之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="51961-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="51961-108">[in]要開始讀取位元組的記憶體資料流內的位移。</span><span class="sxs-lookup"><span data-stu-id="51961-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="51961-109">[out]要將資料複製到其中的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="51961-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="51961-110">緩衝區應該有`countSymbolBytes`的可用空間。</span><span class="sxs-lookup"><span data-stu-id="51961-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="51961-111">[in]要複製的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="51961-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="51961-112">[out]當方法傳回時，會包含實際讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="51961-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51961-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="51961-113">Return Value</span></span>  
 <span data-ttu-id="51961-114">`S_OK`如果已讀取的非零位元組數目。</span><span class="sxs-lookup"><span data-stu-id="51961-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="51961-115">`CORPROF_E_MODULE_IS_DYNAMIC`如果模組使用建立<xref:System.Reflection.Emit>。</span><span class="sxs-lookup"><span data-stu-id="51961-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51961-116">備註</span><span class="sxs-lookup"><span data-stu-id="51961-116">Remarks</span></span>  
 <span data-ttu-id="51961-117">`ReadInMemorySymbols`方法會嘗試讀取`countSymbolBytes`的資料位移處開始`symbolsReadOffset`記憶體資料流中。</span><span class="sxs-lookup"><span data-stu-id="51961-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="51961-118">將資料複製到`pSymbolBytes`，其中應該有`countSymbolBytes`的可用空間。</span><span class="sxs-lookup"><span data-stu-id="51961-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="51961-119">`pCountSymbolsBytesRead` 包含實際讀取，可能會較少的位元組數目比`countSymbolBytes`如果已到達資料流結尾。</span><span class="sxs-lookup"><span data-stu-id="51961-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51961-120">目前的實作不支援這些事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="51961-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="51961-121">如果使用 Reflection.Emit 建立模組，則方法會傳回`CORPROF_E_MODULE_IS_DYNAMIC`。</span><span class="sxs-lookup"><span data-stu-id="51961-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51961-122">需求</span><span class="sxs-lookup"><span data-stu-id="51961-122">Requirements</span></span>  
 <span data-ttu-id="51961-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51961-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51961-124">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51961-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51961-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51961-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51961-126">**.NET framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51961-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51961-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51961-127">See also</span></span>

- [<span data-ttu-id="51961-128">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="51961-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
