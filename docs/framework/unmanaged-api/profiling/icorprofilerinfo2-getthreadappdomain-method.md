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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b351c30c8eadd8c55543f664376cc4c7e5e73af
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481478"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="97529-102">ICorProfilerInfo2::GetThreadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="97529-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="97529-103">取得指定的執行緒目前執行所在的程式碼之應用程式定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="97529-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97529-104">語法</span><span class="sxs-lookup"><span data-stu-id="97529-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97529-105">參數</span><span class="sxs-lookup"><span data-stu-id="97529-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="97529-106">[in]指定在執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="97529-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="97529-107">[out]應用程式定義域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="97529-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97529-108">需求</span><span class="sxs-lookup"><span data-stu-id="97529-108">Requirements</span></span>  
 <span data-ttu-id="97529-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97529-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97529-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97529-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97529-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97529-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97529-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97529-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97529-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97529-113">See also</span></span>
- [<span data-ttu-id="97529-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="97529-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="97529-115">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="97529-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
