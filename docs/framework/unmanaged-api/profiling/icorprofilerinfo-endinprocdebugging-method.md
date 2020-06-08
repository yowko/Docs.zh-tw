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
ms.openlocfilehash: afbb007b6293e6e9cff92281a6f5e93b1e7924ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502973"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="25743-102">ICorProfilerInfo::EndInprocDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="25743-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="25743-103">關閉同進程的偵錯工具會話。</span><span class="sxs-lookup"><span data-stu-id="25743-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="25743-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="25743-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25743-105">語法</span><span class="sxs-lookup"><span data-stu-id="25743-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25743-106">參數</span><span class="sxs-lookup"><span data-stu-id="25743-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="25743-107">在識別偵錯工具會話的值。</span><span class="sxs-lookup"><span data-stu-id="25743-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="25743-108">這個值必須與[ICorProfilerInfo：： BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md)方法中所收到的相同。</span><span class="sxs-lookup"><span data-stu-id="25743-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25743-109">備註</span><span class="sxs-lookup"><span data-stu-id="25743-109">Remarks</span></span>  
 <span data-ttu-id="25743-110">您必須在相同的回呼方法中呼叫[ICorProfilerInfo：： BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) `EndInprocDebugging` 。</span><span class="sxs-lookup"><span data-stu-id="25743-110">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="25743-111">CLR 偵錯工具在 .NET Framework 版本1.0 和1.1 中支援有限的同進程偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="25743-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="25743-112">同進程的偵錯工具已啟用分析工具，以使用偵錯工具開發介面的檢查部分。</span><span class="sxs-lookup"><span data-stu-id="25743-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="25743-113">不過，由於客戶的意見反應，已從版本2.0 中的 .NET Framework 中移除同進程的偵錯工具，並以一組與分析 API 更符合的功能來取代。</span><span class="sxs-lookup"><span data-stu-id="25743-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25743-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="25743-114">Requirements</span></span>  
 <span data-ttu-id="25743-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25743-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25743-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25743-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25743-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25743-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25743-118">**.NET Framework 版本：** 1。0</span><span class="sxs-lookup"><span data-stu-id="25743-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25743-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25743-119">See also</span></span>

- [<span data-ttu-id="25743-120">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="25743-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
