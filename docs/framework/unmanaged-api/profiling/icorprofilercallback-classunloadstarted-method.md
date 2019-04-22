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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0707351d28ef75083b7bfb6ded38bc2a8460131
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136210"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="8371b-102">ICorProfilerCallback::ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="8371b-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="8371b-103">通知分析工具正在卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="8371b-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8371b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8371b-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8371b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8371b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="8371b-106">[in]識別正在卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="8371b-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8371b-107">備註</span><span class="sxs-lookup"><span data-stu-id="8371b-107">Remarks</span></span>  
 <span data-ttu-id="8371b-108">值`classId`不是有效資訊要求之後`ClassUnloadStarted`方法會傳回 — 這是分析工具的最後機會，以取得此類別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8371b-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8371b-109">需求</span><span class="sxs-lookup"><span data-stu-id="8371b-109">Requirements</span></span>  
 <span data-ttu-id="8371b-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8371b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8371b-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8371b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8371b-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8371b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8371b-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8371b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8371b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8371b-114">See also</span></span>

- [<span data-ttu-id="8371b-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8371b-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8371b-116">ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="8371b-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
