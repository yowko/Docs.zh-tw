---
title: ICorProfilerCallback::ModuleUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: fd35f47c004d1ffb235cefe1cd2a1eb2c1fffaef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503311"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="830af-102">ICorProfilerCallback::ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="830af-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="830af-103">通知 profiler 模組已完成卸載。</span><span class="sxs-lookup"><span data-stu-id="830af-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="830af-104">語法</span><span class="sxs-lookup"><span data-stu-id="830af-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="830af-105">參數</span><span class="sxs-lookup"><span data-stu-id="830af-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="830af-106">在已卸載之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="830af-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="830af-107">在HRESULT，指出模組是否已成功卸載。</span><span class="sxs-lookup"><span data-stu-id="830af-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="830af-108">備註</span><span class="sxs-lookup"><span data-stu-id="830af-108">Remarks</span></span>  
 <span data-ttu-id="830af-109">在 `moduleId` [ICorProfilerCallback：： ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md)方法傳回之後，的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="830af-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="830af-110">卸載類別的某些部分可能會在回呼之後繼續進行 `ModuleUnloadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="830af-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="830af-111">中的失敗 HRESULT `hrStatus` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="830af-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="830af-112">不過，中的成功 HRESULT `hrStatus` 只會指出卸載模組的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="830af-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="830af-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="830af-113">Requirements</span></span>  
 <span data-ttu-id="830af-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="830af-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="830af-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="830af-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="830af-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="830af-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="830af-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="830af-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="830af-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="830af-118">See also</span></span>

- [<span data-ttu-id="830af-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="830af-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
