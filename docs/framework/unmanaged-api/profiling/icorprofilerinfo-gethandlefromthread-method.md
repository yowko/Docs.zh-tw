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
ms.openlocfilehash: 94c2c6e01e4188f1fa13c3b6a9f638d4b79a502f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678191"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="207b2-102">ICorProfilerInfo::GetHandleFromThread 方法</span><span class="sxs-lookup"><span data-stu-id="207b2-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="207b2-103">將執行緒的識別碼對應至 Win32 執行緒控制碼。</span><span class="sxs-lookup"><span data-stu-id="207b2-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="207b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="207b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="207b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="207b2-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="207b2-106">在要對應的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="207b2-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="207b2-107">擴展Win32 執行緒控制碼的指標。</span><span class="sxs-lookup"><span data-stu-id="207b2-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="207b2-108">備註</span><span class="sxs-lookup"><span data-stu-id="207b2-108">Remarks</span></span>  

 <span data-ttu-id="207b2-109">分析工具在使用控制碼之前，必須先對其呼叫 Win32 `DuplicateHandle` 函數。</span><span class="sxs-lookup"><span data-stu-id="207b2-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  

 <span data-ttu-id="207b2-110">從這個方法傳回的控制碼是由執行時間所擁有，而且程式碼剖析工具絕對不應該關閉它。</span><span class="sxs-lookup"><span data-stu-id="207b2-110">The handle returned from this method is owned by the runtime and the profiler should never close it.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="207b2-111">需求</span><span class="sxs-lookup"><span data-stu-id="207b2-111">Requirements</span></span>  

 <span data-ttu-id="207b2-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="207b2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="207b2-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="207b2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="207b2-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="207b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="207b2-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="207b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207b2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="207b2-116">See also</span></span>

- [<span data-ttu-id="207b2-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="207b2-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
