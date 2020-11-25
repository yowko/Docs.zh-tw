---
title: ICorProfilerCallback::ClassUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 1c154eee85811796321aea2647db1c8996997576
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700219"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="756f8-102">ICorProfilerCallback::ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="756f8-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>

<span data-ttu-id="756f8-103">通知分析工具有正在卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="756f8-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="756f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="756f8-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="756f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="756f8-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="756f8-106">\[in] 識別正在卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="756f8-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="756f8-107">備註</span><span class="sxs-lookup"><span data-stu-id="756f8-107">Remarks</span></span>  

 <span data-ttu-id="756f8-108">在方法傳回之後，的值對 `classId` 資訊要求而言是不正確 `ClassUnloadStarted` ，這是 profiler 取得這個類別相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="756f8-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="756f8-109">需求</span><span class="sxs-lookup"><span data-stu-id="756f8-109">Requirements</span></span>  

 <span data-ttu-id="756f8-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="756f8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="756f8-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="756f8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="756f8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="756f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="756f8-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="756f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756f8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="756f8-114">See also</span></span>

- [<span data-ttu-id="756f8-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="756f8-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="756f8-116">ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="756f8-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
