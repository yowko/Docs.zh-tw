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
ms.openlocfilehash: c7ad94bf766e0fcdbff95b0766cf68c2196a2c71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503325"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="0243a-102">ICorProfilerCallback::ModuleUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="0243a-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="0243a-103">通知分析工具，模組正在卸載。</span><span class="sxs-lookup"><span data-stu-id="0243a-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0243a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0243a-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="0243a-105">參數</span><span class="sxs-lookup"><span data-stu-id="0243a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="0243a-106">在要卸載之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0243a-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0243a-107">備註</span><span class="sxs-lookup"><span data-stu-id="0243a-107">Remarks</span></span>  
 <span data-ttu-id="0243a-108">在方法傳回之後，的值 `moduleId` 對資訊要求無效 `ModuleUnloadStarted` ，這是分析工具的最後機會取得此模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0243a-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0243a-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="0243a-109">Requirements</span></span>  
 <span data-ttu-id="0243a-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0243a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0243a-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0243a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0243a-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0243a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0243a-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0243a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0243a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0243a-114">See also</span></span>

- [<span data-ttu-id="0243a-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0243a-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0243a-116">ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="0243a-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
