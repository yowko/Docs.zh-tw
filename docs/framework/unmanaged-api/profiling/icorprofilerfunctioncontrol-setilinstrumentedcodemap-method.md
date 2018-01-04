---
title: "ICorProfilerFunctionControl::SetILInstrumentedCodeMap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 580d60fe0a6348a163fef9e215cddfc1bc4302b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="2699e-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap 方法</span><span class="sxs-lookup"><span data-stu-id="2699e-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="2699e-103">使用指定的通用中繼語言 (CIL) 對應項目，設定指定函式的程式碼對應。</span><span class="sxs-lookup"><span data-stu-id="2699e-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2699e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2699e-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2699e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2699e-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="2699e-106">[in] 對應中的項目數。</span><span class="sxs-lookup"><span data-stu-id="2699e-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="2699e-107">[in]COR_IL_MAP 項目的呼叫端配置的陣列。</span><span class="sxs-lookup"><span data-stu-id="2699e-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="2699e-108">這些項目的轉譯為一樣[icorprofilerinfo:: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2699e-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2699e-109">備註</span><span class="sxs-lookup"><span data-stu-id="2699e-109">Remarks</span></span>  
 <span data-ttu-id="2699e-110">設定對應，藉由呼叫這個方法，讓偵錯工具來擷取對應，藉由呼叫[icordebugilcode2:: Getinstrumentedilmap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2699e-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="2699e-111">這也可以讓偵錯工具在計算堆疊追蹤及變數存留期的 IL 位移時於內部使用對應。</span><span class="sxs-lookup"><span data-stu-id="2699e-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2699e-112">需求</span><span class="sxs-lookup"><span data-stu-id="2699e-112">Requirements</span></span>  
 <span data-ttu-id="2699e-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2699e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2699e-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2699e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2699e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2699e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2699e-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2699e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2699e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="2699e-117">See Also</span></span>  
 [<span data-ttu-id="2699e-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="2699e-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
