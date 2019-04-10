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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24b7af4b44d51da06e9d65104f1b469ef1d83b8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219430"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="114a1-102">ICorProfilerInfo::GetInprocInspectionIThisThread 方法</span><span class="sxs-lookup"><span data-stu-id="114a1-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="114a1-103">ICorDebugThread 介面取得的可查詢的物件。</span><span class="sxs-lookup"><span data-stu-id="114a1-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="114a1-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="114a1-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="114a1-105">語法</span><span class="sxs-lookup"><span data-stu-id="114a1-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="114a1-106">參數</span><span class="sxs-lookup"><span data-stu-id="114a1-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="114a1-107">[out](/cpp/atl/iunknown)物件，可以查詢`ICorDebugThread`介面。</span><span class="sxs-lookup"><span data-stu-id="114a1-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="114a1-108">備註</span><span class="sxs-lookup"><span data-stu-id="114a1-108">Remarks</span></span>  
 <span data-ttu-id="114a1-109">Common language runtime (CLR) 偵錯服務支援有限的處理序中的偵錯.NET Framework 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="114a1-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="114a1-110">若要使用偵錯 API 檢查部分的程式碼剖析工具啟用同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="114a1-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="114a1-111">因為客戶的意見反應，而同處理序偵錯已移除從.NET Framework 2.0 版中，並取代為一組更符合程式碼剖析 API 的功能。</span><span class="sxs-lookup"><span data-stu-id="114a1-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="114a1-112">需求</span><span class="sxs-lookup"><span data-stu-id="114a1-112">Requirements</span></span>  
 <span data-ttu-id="114a1-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="114a1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="114a1-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="114a1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="114a1-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="114a1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="114a1-116">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="114a1-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114a1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="114a1-117">See also</span></span>

- [<span data-ttu-id="114a1-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="114a1-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
