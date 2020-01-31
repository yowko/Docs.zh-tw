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
ms.openlocfilehash: 5d9474f78dd8b999a37f60e0698cfd04240b897a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866568"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="fa4e8-102">ICorProfilerCallback::ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="fa4e8-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="fa4e8-103">通知分析工具，類別已完成卸載。</span><span class="sxs-lookup"><span data-stu-id="fa4e8-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa4e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa4e8-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa4e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa4e8-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="fa4e8-106">中的 \[] 可識別已卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="fa4e8-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="fa4e8-107">\[in]） HRESULT，指出是否已成功卸載類別。</span><span class="sxs-lookup"><span data-stu-id="fa4e8-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="fa4e8-108">備註</span><span class="sxs-lookup"><span data-stu-id="fa4e8-108">Remarks</span></span>  
 <span data-ttu-id="fa4e8-109">卸載類別的某些部分可能會在 `ClassUnloadFinished` 回呼之後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="fa4e8-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="fa4e8-110">`hrStatus` 中的失敗 HRESULT 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="fa4e8-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="fa4e8-111">不過，`hrStatus` 中的成功 HRESULT 只會指出卸載類別的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="fa4e8-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa4e8-112">需求</span><span class="sxs-lookup"><span data-stu-id="fa4e8-112">Requirements</span></span>  
 <span data-ttu-id="fa4e8-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa4e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa4e8-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa4e8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa4e8-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa4e8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa4e8-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa4e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4e8-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa4e8-117">See also</span></span>

- [<span data-ttu-id="fa4e8-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fa4e8-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fa4e8-119">ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="fa4e8-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
