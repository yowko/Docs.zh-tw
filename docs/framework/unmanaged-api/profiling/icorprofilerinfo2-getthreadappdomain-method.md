---
title: ICorProfilerInfo2::GetThreadAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: 010b2dff27ac17906e16fe58729facc7a217b43f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703743"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="1068d-102">ICorProfilerInfo2::GetThreadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1068d-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>

<span data-ttu-id="1068d-103">取得指定執行緒目前執行程式碼之應用程式域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1068d-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1068d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1068d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1068d-105">參數</span><span class="sxs-lookup"><span data-stu-id="1068d-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="1068d-106">在指定執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1068d-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="1068d-107">擴展應用程式域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="1068d-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1068d-108">需求</span><span class="sxs-lookup"><span data-stu-id="1068d-108">Requirements</span></span>  

 <span data-ttu-id="1068d-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1068d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1068d-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1068d-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1068d-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1068d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1068d-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1068d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1068d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1068d-113">See also</span></span>

- [<span data-ttu-id="1068d-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="1068d-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1068d-115">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="1068d-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
