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
ms.openlocfilehash: cc8bdfb1e46e5304227a40f869856f07e1f90bed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707486"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="33fd8-102">ICorProfilerInfo::GetInprocInspectionInterface 方法</span><span class="sxs-lookup"><span data-stu-id="33fd8-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>

<span data-ttu-id="33fd8-103">取得可針對 "ICorDebugProcess" 介面進行查詢的物件。</span><span class="sxs-lookup"><span data-stu-id="33fd8-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="33fd8-104">此方法在 .NET Framework 版本2.0 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="33fd8-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33fd8-105">語法</span><span class="sxs-lookup"><span data-stu-id="33fd8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33fd8-106">參數</span><span class="sxs-lookup"><span data-stu-id="33fd8-106">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="33fd8-107">可針對介面進行查詢的[out](/cpp/atl/iunknown)物件 `ICorDebugProcess` 。</span><span class="sxs-lookup"><span data-stu-id="33fd8-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33fd8-108">備註</span><span class="sxs-lookup"><span data-stu-id="33fd8-108">Remarks</span></span>  

 <span data-ttu-id="33fd8-109">Common language runtime (CLR) 偵錯工具開發介面支援在 .NET Framework 1.0 版中進行有限的進程內進行中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="33fd8-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="33fd8-110">同進程的偵錯工具可讓分析工具使用偵錯工具 API 的檢查部分。</span><span class="sxs-lookup"><span data-stu-id="33fd8-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="33fd8-111">由於客戶的意見反應，已從2.0 版中的 .NET Framework 移除同進程的偵錯工具，並以一組與分析 API 更同行的功能取代。</span><span class="sxs-lookup"><span data-stu-id="33fd8-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33fd8-112">需求</span><span class="sxs-lookup"><span data-stu-id="33fd8-112">Requirements</span></span>  

 <span data-ttu-id="33fd8-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33fd8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33fd8-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="33fd8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33fd8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33fd8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33fd8-116">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="33fd8-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33fd8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33fd8-117">See also</span></span>

- [<span data-ttu-id="33fd8-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="33fd8-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
