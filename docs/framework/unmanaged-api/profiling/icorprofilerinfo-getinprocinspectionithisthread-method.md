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
ms.openlocfilehash: 8daa84e3abbbc64c9a48d8957b4ad9c6756d0d8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682077"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="a3f03-102">ICorProfilerInfo::GetInprocInspectionIThisThread 方法</span><span class="sxs-lookup"><span data-stu-id="a3f03-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>

<span data-ttu-id="a3f03-103">取得可針對 ICorDebugThread 介面進行查詢的物件。</span><span class="sxs-lookup"><span data-stu-id="a3f03-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="a3f03-104">此方法在 .NET Framework 版本2.0 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="a3f03-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f03-105">語法</span><span class="sxs-lookup"><span data-stu-id="a3f03-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3f03-106">參數</span><span class="sxs-lookup"><span data-stu-id="a3f03-106">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="a3f03-107">可針對介面進行查詢的[out](/cpp/atl/iunknown)物件 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="a3f03-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3f03-108">備註</span><span class="sxs-lookup"><span data-stu-id="a3f03-108">Remarks</span></span>  

 <span data-ttu-id="a3f03-109">Common language runtime (CLR) 偵錯工具在 .NET Framework 1.0 版中支援有限的同進程處理。</span><span class="sxs-lookup"><span data-stu-id="a3f03-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="a3f03-110">同進程的偵錯工具可讓分析工具使用偵錯工具 API 的檢查部分。</span><span class="sxs-lookup"><span data-stu-id="a3f03-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="a3f03-111">由於客戶的意見反應，已從2.0 版中的 .NET Framework 移除同進程的偵錯工具，並以一組與分析 API 更同行的功能取代。</span><span class="sxs-lookup"><span data-stu-id="a3f03-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3f03-112">需求</span><span class="sxs-lookup"><span data-stu-id="a3f03-112">Requirements</span></span>  

 <span data-ttu-id="a3f03-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f03-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3f03-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3f03-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3f03-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3f03-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3f03-116">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="a3f03-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f03-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f03-117">See also</span></span>

- [<span data-ttu-id="a3f03-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="a3f03-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
