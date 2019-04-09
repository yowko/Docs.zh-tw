---
title: ICorProfilerInfo::EndInprocDebugging 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bcae66fd30c29a0a3c9bd0b5ffc2047efdf3788d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138204"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="888b5-102">ICorProfilerInfo::EndInprocDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="888b5-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="888b5-103">關閉同處理序偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="888b5-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="888b5-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="888b5-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="888b5-105">語法</span><span class="sxs-lookup"><span data-stu-id="888b5-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="888b5-106">參數</span><span class="sxs-lookup"><span data-stu-id="888b5-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="888b5-107">[in]值，這個值識別的偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="888b5-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="888b5-108">此值必須在收到的相同[icorprofilerinfo:: Begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="888b5-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="888b5-109">備註</span><span class="sxs-lookup"><span data-stu-id="888b5-109">Remarks</span></span>  
 <span data-ttu-id="888b5-110">您必須呼叫[icorprofilerinfo:: Begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)和`EndInprocDebugging`內相同的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="888b5-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="888b5-111">CLR 偵錯服務支援有限的處理序中的偵錯.NET framework 1.0 和 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="888b5-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="888b5-112">若要使用偵錯 API 檢查部分的程式碼剖析工具啟用同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="888b5-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="888b5-113">不過，由於客戶的意見反應，同處理序偵錯已移除從.NET Framework 2.0 版中，並取代為一組更符合程式碼剖析 API 的功能。</span><span class="sxs-lookup"><span data-stu-id="888b5-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="888b5-114">需求</span><span class="sxs-lookup"><span data-stu-id="888b5-114">Requirements</span></span>  
 <span data-ttu-id="888b5-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="888b5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="888b5-116">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="888b5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="888b5-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="888b5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="888b5-118">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="888b5-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888b5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="888b5-119">See also</span></span>

- [<span data-ttu-id="888b5-120">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="888b5-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
