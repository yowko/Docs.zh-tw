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
ms.openlocfilehash: 32a69f948b936dd80ab364583dc2928778b34ba0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174404"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="a0b3a-102">ICorProfilerInfo2::GetThreadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="a0b3a-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="a0b3a-103">取得指定的執行緒目前執行所在的程式碼之應用程式定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="a0b3a-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0b3a-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0b3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0b3a-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a0b3a-106">[in]指定在執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="a0b3a-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="a0b3a-107">[out]應用程式定義域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="a0b3a-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0b3a-108">需求</span><span class="sxs-lookup"><span data-stu-id="a0b3a-108">Requirements</span></span>  
 <span data-ttu-id="a0b3a-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b3a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0b3a-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0b3a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0b3a-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0b3a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0b3a-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0b3a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b3a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0b3a-113">See also</span></span>

- [<span data-ttu-id="a0b3a-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="a0b3a-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="a0b3a-115">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="a0b3a-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
