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
ms.openlocfilehash: 9874c8e567a89fd3977be360666c86406f2cd395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455927"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="ce317-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="ce317-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="ce317-103">[受到 [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 和更新版本的支援]</span><span class="sxs-lookup"><span data-stu-id="ce317-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="ce317-104">從記憶體中的符號資料流讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="ce317-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce317-105">語法</span><span class="sxs-lookup"><span data-stu-id="ce317-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce317-106">參數</span><span class="sxs-lookup"><span data-stu-id="ce317-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ce317-107">[in]包含記憶體中資料流之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce317-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="ce317-108">[in]要開始寫入讀取位元組的記憶體中資料流內的位移。</span><span class="sxs-lookup"><span data-stu-id="ce317-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="ce317-109">[out]將資料複製到其中的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="ce317-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="ce317-110">緩衝區應該有`countSymbolBytes`的可用空間。</span><span class="sxs-lookup"><span data-stu-id="ce317-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="ce317-111">[in]要複製的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="ce317-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="ce317-112">[out]當方法傳回時，會包含實際讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="ce317-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce317-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="ce317-113">Return Value</span></span>  
 <span data-ttu-id="ce317-114">`S_OK`如果已讀取的非零位元組數目。</span><span class="sxs-lookup"><span data-stu-id="ce317-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="ce317-115">`CORPROF_E_MODULE_IS_DYNAMIC`如果模組使用建立<xref:System.Reflection.Emit>。</span><span class="sxs-lookup"><span data-stu-id="ce317-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce317-116">備註</span><span class="sxs-lookup"><span data-stu-id="ce317-116">Remarks</span></span>  
 <span data-ttu-id="ce317-117">`ReadInMemorySymbols`方法會嘗試讀取`countSymbolBytes`資料位移處開始的`symbolsReadOffset`記憶體中資料流中。</span><span class="sxs-lookup"><span data-stu-id="ce317-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="ce317-118">將資料複製到`pSymbolBytes`，應該要有`countSymbolBytes`的可用空間。</span><span class="sxs-lookup"><span data-stu-id="ce317-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="ce317-119">`pCountSymbolsBytesRead` 包含實際讀取位元組數，可能會小於比`countSymbolBytes`如果已到達資料流結尾。</span><span class="sxs-lookup"><span data-stu-id="ce317-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce317-120">目前的實作不支援這些事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ce317-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="ce317-121">如果使用 Reflection.Emit 建立模組，則方法會傳回`CORPROF_E_MODULE_IS_DYNAMIC`。</span><span class="sxs-lookup"><span data-stu-id="ce317-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce317-122">需求</span><span class="sxs-lookup"><span data-stu-id="ce317-122">Requirements</span></span>  
 <span data-ttu-id="ce317-123">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce317-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce317-124">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce317-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce317-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce317-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce317-126">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce317-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce317-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce317-127">See Also</span></span>  
 [<span data-ttu-id="ce317-128">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="ce317-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
