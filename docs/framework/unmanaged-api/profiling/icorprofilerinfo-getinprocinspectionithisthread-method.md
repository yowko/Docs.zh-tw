---
title: ICorProfilerInfo::GetInprocInspectionIThisThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: bcc324d0f5cd14e1de9f02c8e6844a5868b70e8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438905"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="c9f52-102">ICorProfilerInfo::GetInprocInspectionIThisThread 方法</span><span class="sxs-lookup"><span data-stu-id="c9f52-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="c9f52-103">Gets an object that can be queried for the ICorDebugThread interface.</span><span class="sxs-lookup"><span data-stu-id="c9f52-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="c9f52-104">This method is obsolete in the .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="c9f52-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f52-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9f52-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9f52-106">參數</span><span class="sxs-lookup"><span data-stu-id="c9f52-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="c9f52-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span><span class="sxs-lookup"><span data-stu-id="c9f52-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9f52-108">備註</span><span class="sxs-lookup"><span data-stu-id="c9f52-108">Remarks</span></span>  
 <span data-ttu-id="c9f52-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span><span class="sxs-lookup"><span data-stu-id="c9f52-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="c9f52-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span><span class="sxs-lookup"><span data-stu-id="c9f52-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="c9f52-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span><span class="sxs-lookup"><span data-stu-id="c9f52-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f52-112">需求</span><span class="sxs-lookup"><span data-stu-id="c9f52-112">Requirements</span></span>  
 <span data-ttu-id="c9f52-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f52-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f52-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9f52-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9f52-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9f52-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9f52-116">**.NET Framework Version:** 1.0</span><span class="sxs-lookup"><span data-stu-id="c9f52-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f52-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9f52-117">See also</span></span>

- [<span data-ttu-id="c9f52-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c9f52-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
