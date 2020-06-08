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
ms.openlocfilehash: f0b118ef109d0adb17a28b60c091390b8e4280c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498657"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="fbeba-102">ICorProfilerInfo::BeginInprocDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="fbeba-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="fbeba-103">初始化同進程的偵錯工具支援。</span><span class="sxs-lookup"><span data-stu-id="fbeba-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="fbeba-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="fbeba-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbeba-105">語法</span><span class="sxs-lookup"><span data-stu-id="fbeba-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbeba-106">參數</span><span class="sxs-lookup"><span data-stu-id="fbeba-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="fbeba-107">在將此值設定為 `true` ，只初始化目前線程的偵錯工具支援; 將它設定為 `false` 可初始化所有線程的偵錯工具支援。</span><span class="sxs-lookup"><span data-stu-id="fbeba-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="fbeba-108">脫銷識別偵錯工具會話之傳回值的指標。</span><span class="sxs-lookup"><span data-stu-id="fbeba-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbeba-109">備註</span><span class="sxs-lookup"><span data-stu-id="fbeba-109">Remarks</span></span>  
 <span data-ttu-id="fbeba-110">CLR 偵錯工具在 .NET Framework 版本1.0 和1.1 中支援有限的同進程偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="fbeba-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="fbeba-111">同進程的偵錯工具已啟用分析工具，以使用偵錯工具開發介面的檢查部分。</span><span class="sxs-lookup"><span data-stu-id="fbeba-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="fbeba-112">不過，由於客戶的意見反應，已從版本2.0 中的 .NET Framework 中移除同進程的偵錯工具，並以一組與分析 API 更符合的功能來取代。</span><span class="sxs-lookup"><span data-stu-id="fbeba-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbeba-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="fbeba-113">Requirements</span></span>  
 <span data-ttu-id="fbeba-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbeba-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbeba-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fbeba-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fbeba-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbeba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbeba-117">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="fbeba-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbeba-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbeba-118">See also</span></span>

- [<span data-ttu-id="fbeba-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fbeba-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
