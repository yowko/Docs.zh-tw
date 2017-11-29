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
ms.openlocfilehash: be925bbbcc86785feae28353dbc6563974aae2c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="dc9af-102">ICorProfilerInfo::GetHandleFromThread 方法</span><span class="sxs-lookup"><span data-stu-id="dc9af-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="dc9af-103">將執行緒的 ID 對應至 Win32 執行緒控制代碼。</span><span class="sxs-lookup"><span data-stu-id="dc9af-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9af-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc9af-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc9af-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc9af-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="dc9af-106">[in]要對應的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="dc9af-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="dc9af-107">[out]Win32 執行緒控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="dc9af-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc9af-108">備註</span><span class="sxs-lookup"><span data-stu-id="dc9af-108">Remarks</span></span>  
 <span data-ttu-id="dc9af-109">分析工具必須呼叫 Win32`DuplicateHandle`函式上使用它之前的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="dc9af-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc9af-110">需求</span><span class="sxs-lookup"><span data-stu-id="dc9af-110">Requirements</span></span>  
 <span data-ttu-id="dc9af-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc9af-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc9af-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc9af-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc9af-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc9af-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc9af-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc9af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc9af-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc9af-115">See Also</span></span>  
 [<span data-ttu-id="dc9af-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="dc9af-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
