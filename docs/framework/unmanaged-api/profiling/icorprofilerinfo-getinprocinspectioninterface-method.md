---
title: "ICorProfilerInfo::GetInprocInspectionInterface 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9088389df33b079fe2275f5c7e642a055fa8ee51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="ad6ba-102">ICorProfilerInfo::GetInprocInspectionInterface 方法</span><span class="sxs-lookup"><span data-stu-id="ad6ba-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="ad6ba-103">取得物件，可以查詢 「 ICorDebugProcess"介面。</span><span class="sxs-lookup"><span data-stu-id="ad6ba-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="ad6ba-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="ad6ba-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad6ba-105">語法</span><span class="sxs-lookup"><span data-stu-id="ad6ba-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad6ba-106">參數</span><span class="sxs-lookup"><span data-stu-id="ad6ba-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="ad6ba-107">[out](/cpp/atl/iunknown)可以查詢的物件`ICorDebugProcess`介面。</span><span class="sxs-lookup"><span data-stu-id="ad6ba-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad6ba-108">備註</span><span class="sxs-lookup"><span data-stu-id="ad6ba-108">Remarks</span></span>  
 <span data-ttu-id="ad6ba-109">Common language runtime (CLR) 偵錯應用程式開發介面支援有限的處理序中的偵錯.NET Framework 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="ad6ba-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="ad6ba-110">若要使用偵錯 API 檢查部份程式碼剖析工具啟用同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="ad6ba-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="ad6ba-111">客戶的意見反應，因為同處理序偵錯具有已經從.NET Framework 2.0 版中移除和取代的功能與程式碼剖析 API 對齊多個一組。</span><span class="sxs-lookup"><span data-stu-id="ad6ba-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad6ba-112">需求</span><span class="sxs-lookup"><span data-stu-id="ad6ba-112">Requirements</span></span>  
 <span data-ttu-id="ad6ba-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad6ba-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad6ba-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad6ba-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad6ba-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad6ba-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad6ba-116">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="ad6ba-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6ba-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad6ba-117">See Also</span></span>  
 [<span data-ttu-id="ad6ba-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ad6ba-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
