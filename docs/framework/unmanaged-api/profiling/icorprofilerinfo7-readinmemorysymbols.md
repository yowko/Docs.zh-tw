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
ms.openlocfilehash: 6917900b7494550992dfa82f45ed0140f95e68cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733616"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="73a1c-102">ICorProfilerInfo7：： ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="73a1c-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>

<span data-ttu-id="73a1c-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="73a1c-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="73a1c-104">從記憶體中的符號資料流程讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="73a1c-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a1c-105">語法</span><span class="sxs-lookup"><span data-stu-id="73a1c-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73a1c-106">參數</span><span class="sxs-lookup"><span data-stu-id="73a1c-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="73a1c-107">在包含記憶體中資料流程之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="73a1c-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="73a1c-108">在記憶體內資料流程中要開始讀取位元組的位移。</span><span class="sxs-lookup"><span data-stu-id="73a1c-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="73a1c-109">擴展要將資料複製到其中的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="73a1c-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="73a1c-110">緩衝區應該有 `countSymbolBytes` 可用的空間。</span><span class="sxs-lookup"><span data-stu-id="73a1c-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="73a1c-111">在要複製的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="73a1c-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="73a1c-112">擴展當方法傳回時，會包含所讀取的實際位元組數目。</span><span class="sxs-lookup"><span data-stu-id="73a1c-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73a1c-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="73a1c-113">Return Value</span></span>  

 <span data-ttu-id="73a1c-114">`S_OK`如果讀取了非零的位元組數目，則為。</span><span class="sxs-lookup"><span data-stu-id="73a1c-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="73a1c-115">`CORPROF_E_MODULE_IS_DYNAMIC`如果模組是使用建立的，則為 <xref:System.Reflection.Emit> 。</span><span class="sxs-lookup"><span data-stu-id="73a1c-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73a1c-116">備註</span><span class="sxs-lookup"><span data-stu-id="73a1c-116">Remarks</span></span>  

 <span data-ttu-id="73a1c-117">`ReadInMemorySymbols`方法會嘗試 `countSymbolBytes` 從 `symbolsReadOffset` 記憶體內資料流程內的位移開始讀取資料。</span><span class="sxs-lookup"><span data-stu-id="73a1c-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="73a1c-118">資料會複製到 `pSymbolBytes` ，且預期會有 `countSymbolBytes` 可用的空間。</span><span class="sxs-lookup"><span data-stu-id="73a1c-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="73a1c-119">`pCountSymbolsBytesRead` 包含讀取的實際位元組數目， `countSymbolBytes` 如果到達資料流程末端，則可能小於。</span><span class="sxs-lookup"><span data-stu-id="73a1c-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73a1c-120">目前的執行不支援反映。發出。</span><span class="sxs-lookup"><span data-stu-id="73a1c-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="73a1c-121">如果模組是使用反映來建立，則方法會傳回 `CORPROF_E_MODULE_IS_DYNAMIC` 。</span><span class="sxs-lookup"><span data-stu-id="73a1c-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73a1c-122">需求</span><span class="sxs-lookup"><span data-stu-id="73a1c-122">Requirements</span></span>  

 <span data-ttu-id="73a1c-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73a1c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73a1c-124">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73a1c-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73a1c-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73a1c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73a1c-126">**.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73a1c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a1c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73a1c-127">See also</span></span>

- [<span data-ttu-id="73a1c-128">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="73a1c-128">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
