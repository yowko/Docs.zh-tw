---
title: ICorProfilerInfo4::GetFunctionFromIP2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18099e6e658391d6dae7a666cd0cebefa5859b1a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110530"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="0de68-102">ICorProfilerInfo4::GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="0de68-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="0de68-103">Managed 程式碼指令指標會對應至函式的 JIT 重新編譯版本。</span><span class="sxs-lookup"><span data-stu-id="0de68-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de68-104">語法</span><span class="sxs-lookup"><span data-stu-id="0de68-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0de68-105">參數</span><span class="sxs-lookup"><span data-stu-id="0de68-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="0de68-106">[in]在 managed 程式碼指令指標。</span><span class="sxs-lookup"><span data-stu-id="0de68-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="0de68-107">[out]函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="0de68-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="0de68-108">[out]函式的 JIT 重新編譯版本的身分識別。</span><span class="sxs-lookup"><span data-stu-id="0de68-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0de68-109">備註</span><span class="sxs-lookup"><span data-stu-id="0de68-109">Remarks</span></span>  
 `GetFunctionFromIP2` <span data-ttu-id="0de68-110">類似於`GetFunctionFromIP`，只不過它取得的 JIT 重新編譯識別碼而不是包含指定的 IP 位址的函式的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="0de68-110">is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  `GetFunctionFromIP2` <span data-ttu-id="0de68-111">可以觸發記憶體回收，而`GetFunctionFromIP`不會。</span><span class="sxs-lookup"><span data-stu-id="0de68-111">can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="0de68-112">如需詳細資訊，請參閱 < [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)。</span><span class="sxs-lookup"><span data-stu-id="0de68-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de68-113">需求</span><span class="sxs-lookup"><span data-stu-id="0de68-113">Requirements</span></span>  
 <span data-ttu-id="0de68-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0de68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de68-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0de68-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0de68-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0de68-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0de68-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0de68-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0de68-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0de68-118">See also</span></span>

- [<span data-ttu-id="0de68-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="0de68-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
