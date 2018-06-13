---
title: ICorProfilerInfo::BeginInprocDebugging 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82e798e1a31f771c63e71f2a85f8cbb684b237bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462386"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="b7aee-102">ICorProfilerInfo::BeginInprocDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="b7aee-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="b7aee-103">初始化同處理序偵錯支援。</span><span class="sxs-lookup"><span data-stu-id="b7aee-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="b7aee-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="b7aee-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7aee-105">語法</span><span class="sxs-lookup"><span data-stu-id="b7aee-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7aee-106">參數</span><span class="sxs-lookup"><span data-stu-id="b7aee-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="b7aee-107">[in]將此值設定為`true`初始化偵錯支援只在目前的執行緒; 將它設定為`false`初始化偵錯支援的所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="b7aee-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="b7aee-108">[out]要傳回的值，可識別偵錯工作階段的指標。</span><span class="sxs-lookup"><span data-stu-id="b7aee-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7aee-109">備註</span><span class="sxs-lookup"><span data-stu-id="b7aee-109">Remarks</span></span>  
 <span data-ttu-id="b7aee-110">CLR 偵錯服務支援有限的處理序中的偵錯.NET framework 1.0 和 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="b7aee-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="b7aee-111">若要使用偵錯 API 檢查部份程式碼剖析工具啟用同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="b7aee-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="b7aee-112">不過，由於客戶的意見反應，同處理序偵錯具有已從.NET Framework 2.0 版中移除和取代的功能與程式碼剖析 API 對齊多個一組。</span><span class="sxs-lookup"><span data-stu-id="b7aee-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7aee-113">需求</span><span class="sxs-lookup"><span data-stu-id="b7aee-113">Requirements</span></span>  
 <span data-ttu-id="b7aee-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7aee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7aee-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7aee-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7aee-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7aee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7aee-117">**.NET framework 版本：** 1.0</span><span class="sxs-lookup"><span data-stu-id="b7aee-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7aee-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7aee-118">See Also</span></span>  
 [<span data-ttu-id="b7aee-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="b7aee-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
