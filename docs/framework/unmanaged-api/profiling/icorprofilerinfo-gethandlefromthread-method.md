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
ms.openlocfilehash: 632a9070eab227bc48ce76c51ea08f98060d680d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722529"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="bf596-102">ICorProfilerInfo::GetHandleFromThread 方法</span><span class="sxs-lookup"><span data-stu-id="bf596-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="bf596-103">將執行緒的識別碼對應至 Win32 執行緒控制碼。</span><span class="sxs-lookup"><span data-stu-id="bf596-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf596-104">語法</span><span class="sxs-lookup"><span data-stu-id="bf596-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf596-105">參數</span><span class="sxs-lookup"><span data-stu-id="bf596-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="bf596-106">在要對應的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="bf596-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="bf596-107">擴展Win32 執行緒控制碼的指標。</span><span class="sxs-lookup"><span data-stu-id="bf596-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf596-108">備註</span><span class="sxs-lookup"><span data-stu-id="bf596-108">Remarks</span></span>  

 <span data-ttu-id="bf596-109">分析工具在使用控制碼之前，必須先對其呼叫 Win32 `DuplicateHandle` 函數。</span><span class="sxs-lookup"><span data-stu-id="bf596-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf596-110">需求</span><span class="sxs-lookup"><span data-stu-id="bf596-110">Requirements</span></span>  

 <span data-ttu-id="bf596-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bf596-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf596-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf596-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf596-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf596-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf596-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf596-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf596-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf596-115">See also</span></span>

- [<span data-ttu-id="bf596-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="bf596-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
