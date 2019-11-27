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
ms.openlocfilehash: d3fcd859fb11f6a0c660751f16fa175e19e9d03b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439003"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="18b1e-102">ICorProfilerInfo::GetInprocInspectionInterface 方法</span><span class="sxs-lookup"><span data-stu-id="18b1e-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="18b1e-103">取得可查詢 "ICorDebugProcess" 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="18b1e-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="18b1e-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="18b1e-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b1e-105">語法</span><span class="sxs-lookup"><span data-stu-id="18b1e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18b1e-106">參數</span><span class="sxs-lookup"><span data-stu-id="18b1e-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="18b1e-107">[out](/cpp/atl/iunknown)物件，可查詢 `ICorDebugProcess` 介面。</span><span class="sxs-lookup"><span data-stu-id="18b1e-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18b1e-108">備註</span><span class="sxs-lookup"><span data-stu-id="18b1e-108">Remarks</span></span>  
 <span data-ttu-id="18b1e-109">Common language runtime （CLR）偵錯工具開發介面在 .NET Framework 版本1.0 中支援有限的同進程偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="18b1e-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="18b1e-110">同進程的偵錯工具已啟用分析工具，以使用偵錯工具開發介面的檢查部分。</span><span class="sxs-lookup"><span data-stu-id="18b1e-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="18b1e-111">由於客戶意見反應的結果，已從版本2.0 中的 .NET Framework 中移除同進程的偵錯工具，並以一組與分析 API 更符合的功能來取代。</span><span class="sxs-lookup"><span data-stu-id="18b1e-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b1e-112">需求</span><span class="sxs-lookup"><span data-stu-id="18b1e-112">Requirements</span></span>  
 <span data-ttu-id="18b1e-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18b1e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b1e-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="18b1e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18b1e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18b1e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18b1e-116">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="18b1e-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b1e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18b1e-117">See also</span></span>

- [<span data-ttu-id="18b1e-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="18b1e-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
