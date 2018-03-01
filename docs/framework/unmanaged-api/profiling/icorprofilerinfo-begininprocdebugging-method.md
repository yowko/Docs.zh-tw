---
title: "ICorProfilerInfo::BeginInprocDebugging 方法"
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
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91306bbea7b099f7e9e408f8bf69625f1d7da68e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="520af-102">ICorProfilerInfo::BeginInprocDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="520af-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="520af-103">初始化同處理序偵錯支援。</span><span class="sxs-lookup"><span data-stu-id="520af-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="520af-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="520af-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="520af-105">語法</span><span class="sxs-lookup"><span data-stu-id="520af-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="520af-106">參數</span><span class="sxs-lookup"><span data-stu-id="520af-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="520af-107">[in]將此值設定為`true`初始化偵錯支援只在目前的執行緒; 將它設定為`false`初始化偵錯支援的所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="520af-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="520af-108">[out]要傳回的值，可識別偵錯工作階段的指標。</span><span class="sxs-lookup"><span data-stu-id="520af-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="520af-109">備註</span><span class="sxs-lookup"><span data-stu-id="520af-109">Remarks</span></span>  
 <span data-ttu-id="520af-110">CLR 偵錯服務支援有限的處理序中的偵錯.NET framework 1.0 和 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="520af-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="520af-111">若要使用偵錯 API 檢查部份程式碼剖析工具啟用同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="520af-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="520af-112">不過，由於客戶的意見反應，同處理序偵錯具有已從.NET Framework 2.0 版中移除和取代的功能與程式碼剖析 API 對齊多個一組。</span><span class="sxs-lookup"><span data-stu-id="520af-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="520af-113">需求</span><span class="sxs-lookup"><span data-stu-id="520af-113">Requirements</span></span>  
 <span data-ttu-id="520af-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="520af-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="520af-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="520af-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="520af-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="520af-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="520af-117">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="520af-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520af-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="520af-118">See Also</span></span>  
 [<span data-ttu-id="520af-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="520af-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
