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
ms.openlocfilehash: 8c133338ec0edac19f49d435df41e3081c486f51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948457"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="4069c-102">ICorProfilerInfo4::GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="4069c-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="4069c-103">將 managed 程式碼指令指標對應至 JIT 重新編譯的函式版本。</span><span class="sxs-lookup"><span data-stu-id="4069c-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4069c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4069c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4069c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4069c-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="4069c-106">在Managed 程式碼中的指令指標。</span><span class="sxs-lookup"><span data-stu-id="4069c-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="4069c-107">脫銷函數識別碼。</span><span class="sxs-lookup"><span data-stu-id="4069c-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="4069c-108">脫銷函式之 JIT 重新編譯版本的識別。</span><span class="sxs-lookup"><span data-stu-id="4069c-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4069c-109">備註</span><span class="sxs-lookup"><span data-stu-id="4069c-109">Remarks</span></span>  
 <span data-ttu-id="4069c-110">`GetFunctionFromIP2`類似`GetFunctionFromIP`于, 不同之處在于它會取得 JIT 重新編譯的識別碼, 而不是包含指定之 IP 位址的函式的函數識別碼。</span><span class="sxs-lookup"><span data-stu-id="4069c-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4069c-111">`GetFunctionFromIP2`可以觸發垃圾收集, 而`GetFunctionFromIP`則不會。</span><span class="sxs-lookup"><span data-stu-id="4069c-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="4069c-112">如需詳細資訊, 請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)。</span><span class="sxs-lookup"><span data-stu-id="4069c-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4069c-113">需求</span><span class="sxs-lookup"><span data-stu-id="4069c-113">Requirements</span></span>  
 <span data-ttu-id="4069c-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4069c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4069c-115">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="4069c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4069c-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4069c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4069c-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4069c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4069c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4069c-118">See also</span></span>

- [<span data-ttu-id="4069c-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4069c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
