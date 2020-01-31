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
ms.openlocfilehash: 0ab383f0968061667b3580a2058687eecda99dde
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869994"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="586ea-102">ICorProfilerInfo::GetInprocInspectionIThisThread 方法</span><span class="sxs-lookup"><span data-stu-id="586ea-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="586ea-103">取得可針對 ICorDebugThread 介面查詢的物件。</span><span class="sxs-lookup"><span data-stu-id="586ea-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="586ea-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="586ea-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586ea-105">語法</span><span class="sxs-lookup"><span data-stu-id="586ea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="586ea-106">參數</span><span class="sxs-lookup"><span data-stu-id="586ea-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="586ea-107">[out](/cpp/atl/iunknown)物件，可查詢 `ICorDebugThread` 介面。</span><span class="sxs-lookup"><span data-stu-id="586ea-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="586ea-108">備註</span><span class="sxs-lookup"><span data-stu-id="586ea-108">Remarks</span></span>  
 <span data-ttu-id="586ea-109">Common language runtime （CLR）偵錯工具在 .NET Framework 版本1.0 中支援有限的同進程偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="586ea-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="586ea-110">同進程的偵錯工具已啟用分析工具，以使用偵錯工具開發介面的檢查部分。</span><span class="sxs-lookup"><span data-stu-id="586ea-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="586ea-111">由於客戶意見反應的結果，已從版本2.0 中的 .NET Framework 中移除同進程的偵錯工具，並以一組與分析 API 更符合的功能來取代。</span><span class="sxs-lookup"><span data-stu-id="586ea-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="586ea-112">需求</span><span class="sxs-lookup"><span data-stu-id="586ea-112">Requirements</span></span>  
 <span data-ttu-id="586ea-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="586ea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="586ea-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="586ea-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="586ea-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="586ea-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="586ea-116">**.NET Framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="586ea-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="586ea-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="586ea-117">See also</span></span>

- [<span data-ttu-id="586ea-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="586ea-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
