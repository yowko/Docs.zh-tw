---
title: ICorProfilerInfo::GetHandleFromThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9658ad8a1963d3747fb7c23dce84790a30b17db3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453218"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="1c600-102">ICorProfilerInfo::GetHandleFromThread 方法</span><span class="sxs-lookup"><span data-stu-id="1c600-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="1c600-103">將執行緒的 ID 對應至 Win32 執行緒控制代碼。</span><span class="sxs-lookup"><span data-stu-id="1c600-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c600-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c600-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c600-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c600-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="1c600-106">[in]要對應的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="1c600-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="1c600-107">[out]Win32 執行緒控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="1c600-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c600-108">備註</span><span class="sxs-lookup"><span data-stu-id="1c600-108">Remarks</span></span>  
 <span data-ttu-id="1c600-109">分析工具必須呼叫 Win32`DuplicateHandle`函式上使用它之前的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="1c600-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c600-110">需求</span><span class="sxs-lookup"><span data-stu-id="1c600-110">Requirements</span></span>  
 <span data-ttu-id="1c600-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c600-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c600-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c600-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c600-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c600-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c600-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c600-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c600-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c600-115">See Also</span></span>  
 [<span data-ttu-id="1c600-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="1c600-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
