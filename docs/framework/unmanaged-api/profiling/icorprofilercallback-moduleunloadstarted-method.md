---
title: ICorProfilerCallback::ModuleUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: 12d5f7e073337af6034b8f313a2e0161620a65ea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720950"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="d91b7-102">ICorProfilerCallback::ModuleUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="d91b7-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>

<span data-ttu-id="d91b7-103">通知分析工具正在卸載模組。</span><span class="sxs-lookup"><span data-stu-id="d91b7-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d91b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="d91b7-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="d91b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="d91b7-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="d91b7-106">在要卸載之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d91b7-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d91b7-107">備註</span><span class="sxs-lookup"><span data-stu-id="d91b7-107">Remarks</span></span>  

 <span data-ttu-id="d91b7-108">在方法傳回之後，的值對 `moduleId` 資訊要求而言是不正確 `ModuleUnloadStarted` ，這是 profiler 取得此課程模組相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="d91b7-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d91b7-109">需求</span><span class="sxs-lookup"><span data-stu-id="d91b7-109">Requirements</span></span>  

 <span data-ttu-id="d91b7-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d91b7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d91b7-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d91b7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d91b7-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d91b7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d91b7-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d91b7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d91b7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d91b7-114">See also</span></span>

- [<span data-ttu-id="d91b7-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d91b7-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d91b7-116">ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="d91b7-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
