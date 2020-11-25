---
title: ICorProfilerInfo::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: 2e24d72c8be1ace10b2feb15101ed8f83db386c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724087"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="4b6ec-102">ICorProfilerInfo::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="4b6ec-102">ICorProfilerInfo::GetThreadContext Method</span></span>

<span data-ttu-id="4b6ec-103">取得目前與指定的執行緒相關聯的內容身分識別。</span><span class="sxs-lookup"><span data-stu-id="4b6ec-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b6ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b6ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b6ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b6ec-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="4b6ec-106">在執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b6ec-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="4b6ec-107">擴展目前與指定的執行緒相關聯之內容識別碼的指標。</span><span class="sxs-lookup"><span data-stu-id="4b6ec-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="4b6ec-108">如果執行緒目前沒有相關聯的內容，此函數將會傳回 CORPROF_E_DATAINCOMPLETE。</span><span class="sxs-lookup"><span data-stu-id="4b6ec-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b6ec-109">需求</span><span class="sxs-lookup"><span data-stu-id="4b6ec-109">Requirements</span></span>  

 <span data-ttu-id="4b6ec-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b6ec-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b6ec-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b6ec-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b6ec-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b6ec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b6ec-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b6ec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b6ec-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b6ec-114">See also</span></span>

- [<span data-ttu-id="4b6ec-115">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4b6ec-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
