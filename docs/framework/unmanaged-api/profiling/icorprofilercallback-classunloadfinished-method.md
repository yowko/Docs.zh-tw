---
title: ICorProfilerCallback::ClassUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 14eb90c707618796d6d62ed2ec5710ceba31ba6c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500373"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="abed3-102">ICorProfilerCallback::ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="abed3-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="abed3-103">通知分析工具，類別已完成卸載。</span><span class="sxs-lookup"><span data-stu-id="abed3-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abed3-104">語法</span><span class="sxs-lookup"><span data-stu-id="abed3-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abed3-105">參數</span><span class="sxs-lookup"><span data-stu-id="abed3-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="abed3-106">\[在中，識別已卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="abed3-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="abed3-107">\[in] 表示是否已成功卸載類別的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="abed3-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="abed3-108">備註</span><span class="sxs-lookup"><span data-stu-id="abed3-108">Remarks</span></span>  
 <span data-ttu-id="abed3-109">卸載類別的某些部分可能會在回呼之後繼續進行 `ClassUnloadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="abed3-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="abed3-110">中的失敗 HRESULT `hrStatus` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="abed3-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="abed3-111">不過，中的成功 HRESULT `hrStatus` 只會指出卸載類別的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="abed3-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abed3-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="abed3-112">Requirements</span></span>  
 <span data-ttu-id="abed3-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abed3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abed3-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abed3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abed3-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abed3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abed3-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abed3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abed3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abed3-117">See also</span></span>

- [<span data-ttu-id="abed3-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="abed3-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="abed3-119">ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="abed3-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
