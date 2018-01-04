---
title: "ICorProfilerInfo::GetHandleFromThread 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetHandleFromThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 465fb61d17269873b3a2aa2f323086f209cab946
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="ead8e-102">ICorProfilerInfo::GetHandleFromThread 方法</span><span class="sxs-lookup"><span data-stu-id="ead8e-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="ead8e-103">將執行緒的 ID 對應至 Win32 執行緒控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ead8e-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="ead8e-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ead8e-105">參數</span><span class="sxs-lookup"><span data-stu-id="ead8e-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ead8e-106">[in]要對應的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="ead8e-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="ead8e-107">[out]Win32 執行緒控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="ead8e-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ead8e-108">備註</span><span class="sxs-lookup"><span data-stu-id="ead8e-108">Remarks</span></span>  
 <span data-ttu-id="ead8e-109">分析工具必須呼叫 Win32`DuplicateHandle`函式上使用它之前的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ead8e-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ead8e-110">需求</span><span class="sxs-lookup"><span data-stu-id="ead8e-110">Requirements</span></span>  
 <span data-ttu-id="ead8e-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ead8e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ead8e-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ead8e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ead8e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ead8e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ead8e-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ead8e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead8e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ead8e-115">See Also</span></span>  
 [<span data-ttu-id="ead8e-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ead8e-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
