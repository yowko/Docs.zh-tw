---
title: ICorProfilerInfo::GetInprocInspectionInterface 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67a680727e824cbe29b9e022e00d661e8694f153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780560"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="58959-102">ICorProfilerInfo::GetInprocInspectionInterface 方法</span><span class="sxs-lookup"><span data-stu-id="58959-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="58959-103">取得"ICorDebugProcess 」 介面可查詢的物件。</span><span class="sxs-lookup"><span data-stu-id="58959-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="58959-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="58959-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58959-105">語法</span><span class="sxs-lookup"><span data-stu-id="58959-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58959-106">參數</span><span class="sxs-lookup"><span data-stu-id="58959-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="58959-107">[out](/cpp/atl/iunknown)物件，可以查詢`ICorDebugProcess`介面。</span><span class="sxs-lookup"><span data-stu-id="58959-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58959-108">備註</span><span class="sxs-lookup"><span data-stu-id="58959-108">Remarks</span></span>  
 <span data-ttu-id="58959-109">Common language runtime (CLR) 偵錯 API 支援有限的處理序中的偵錯.NET Framework 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="58959-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="58959-110">若要使用偵錯 API 檢查部分的程式碼剖析工具啟用同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="58959-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="58959-111">因為客戶的意見反應，而同處理序偵錯已移除從.NET Framework 2.0 版中，並取代為一組更符合程式碼剖析 API 的功能。</span><span class="sxs-lookup"><span data-stu-id="58959-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58959-112">需求</span><span class="sxs-lookup"><span data-stu-id="58959-112">Requirements</span></span>  
 <span data-ttu-id="58959-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58959-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58959-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58959-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58959-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58959-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58959-116">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="58959-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58959-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58959-117">See also</span></span>

- [<span data-ttu-id="58959-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="58959-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
