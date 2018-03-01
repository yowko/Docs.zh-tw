---
title: "ICorProfilerInfo::EndInprocDebugging 方法"
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
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a36c557d9ab2fa661808aa2f0be942d11ea9fa61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="edc21-102">ICorProfilerInfo::EndInprocDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="edc21-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="edc21-103">關閉同處理序的偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="edc21-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="edc21-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="edc21-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc21-105">語法</span><span class="sxs-lookup"><span data-stu-id="edc21-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edc21-106">參數</span><span class="sxs-lookup"><span data-stu-id="edc21-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="edc21-107">[in]可識別偵錯工作階段的值。</span><span class="sxs-lookup"><span data-stu-id="edc21-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="edc21-108">這個值必須是相同中收到[icorprofilerinfo:: Begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="edc21-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edc21-109">備註</span><span class="sxs-lookup"><span data-stu-id="edc21-109">Remarks</span></span>  
 <span data-ttu-id="edc21-110">您必須呼叫[icorprofilerinfo:: Begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)和`EndInprocDebugging`內相同的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="edc21-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="edc21-111">CLR 偵錯服務支援有限的處理序中的偵錯.NET framework 1.0 和 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="edc21-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="edc21-112">若要使用偵錯 API 檢查部份程式碼剖析工具啟用同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="edc21-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="edc21-113">不過，由於客戶的意見反應，同處理序偵錯具有已從.NET Framework 2.0 版中移除和取代的功能與程式碼剖析 API 對齊多個一組。</span><span class="sxs-lookup"><span data-stu-id="edc21-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edc21-114">需求</span><span class="sxs-lookup"><span data-stu-id="edc21-114">Requirements</span></span>  
 <span data-ttu-id="edc21-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edc21-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edc21-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="edc21-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="edc21-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edc21-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edc21-118">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="edc21-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc21-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="edc21-119">See Also</span></span>  
 [<span data-ttu-id="edc21-120">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="edc21-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
