---
title: "ICorProfilerInfo::GetThreadInfo 方法"
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
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ab887cf4aaded260903cf1b91498c7641eeb0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="a9f87-102">ICorProfilerInfo::GetThreadInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a9f87-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="a9f87-103">取得指定執行緒的目前 Win32 執行緒識別。</span><span class="sxs-lookup"><span data-stu-id="a9f87-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9f87-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9f87-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9f87-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9f87-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a9f87-106">[in]要取得目前的 Win32 識別碼。 執行緒的識別碼</span><span class="sxs-lookup"><span data-stu-id="a9f87-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="a9f87-107">[out]指向指定的執行緒目前的 Win32 執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a9f87-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9f87-108">需求</span><span class="sxs-lookup"><span data-stu-id="a9f87-108">Requirements</span></span>  
 <span data-ttu-id="a9f87-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9f87-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9f87-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9f87-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9f87-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9f87-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9f87-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9f87-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f87-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9f87-113">See Also</span></span>  
 [<span data-ttu-id="a9f87-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="a9f87-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
