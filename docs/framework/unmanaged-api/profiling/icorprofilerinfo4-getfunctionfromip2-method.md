---
title: "ICorProfilerInfo4::GetFunctionFromIP2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetFunctionFromIP2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2173326c5c67d1f4d3a8e28f84508fd6affb8299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="3995c-102">ICorProfilerInfo4::GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="3995c-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="3995c-103">將 managed 程式碼指令指標對應至函式的 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="3995c-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3995c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3995c-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3995c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3995c-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="3995c-106">[in]指令指標在 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="3995c-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="3995c-107">[out]函式 id。</span><span class="sxs-lookup"><span data-stu-id="3995c-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="3995c-108">[out]函式的 JIT 重新編譯版本的身分識別。</span><span class="sxs-lookup"><span data-stu-id="3995c-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3995c-109">備註</span><span class="sxs-lookup"><span data-stu-id="3995c-109">Remarks</span></span>  
 <span data-ttu-id="3995c-110">`GetFunctionFromIP2`類似於`GetFunctionFromIP`，不同之處在於它取得的 JIT 重新編譯識別碼而非包含指定的 IP 位址的函式的函式 ID。</span><span class="sxs-lookup"><span data-stu-id="3995c-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3995c-111">`GetFunctionFromIP2`可能觸發記憶體回收，而`GetFunctionFromIP`則不會。</span><span class="sxs-lookup"><span data-stu-id="3995c-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="3995c-112">如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)。</span><span class="sxs-lookup"><span data-stu-id="3995c-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3995c-113">需求</span><span class="sxs-lookup"><span data-stu-id="3995c-113">Requirements</span></span>  
 <span data-ttu-id="3995c-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3995c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3995c-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3995c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3995c-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3995c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3995c-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3995c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3995c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3995c-118">See Also</span></span>  
 [<span data-ttu-id="3995c-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="3995c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
