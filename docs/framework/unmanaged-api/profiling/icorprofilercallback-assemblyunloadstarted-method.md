---
title: ICorProfilerCallback::AssemblyUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a45c757a9176c77c7dbf58333b66d9b26514265
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471208"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="7af95-102">ICorProfilerCallback::AssemblyUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="7af95-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="7af95-103">通知分析工具正在卸載組件。</span><span class="sxs-lookup"><span data-stu-id="7af95-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af95-104">語法</span><span class="sxs-lookup"><span data-stu-id="7af95-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7af95-105">參數</span><span class="sxs-lookup"><span data-stu-id="7af95-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="7af95-106">[in]識別正在卸載組件。</span><span class="sxs-lookup"><span data-stu-id="7af95-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7af95-107">備註</span><span class="sxs-lookup"><span data-stu-id="7af95-107">Remarks</span></span>  
 <span data-ttu-id="7af95-108">值`assemblyId`不是有效資訊要求之後`AssemblyUnloadStarted`方法會傳回 — 這是要取得這個組件的相關資訊的分析工具的最後機會。</span><span class="sxs-lookup"><span data-stu-id="7af95-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7af95-109">需求</span><span class="sxs-lookup"><span data-stu-id="7af95-109">Requirements</span></span>  
 <span data-ttu-id="7af95-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7af95-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7af95-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7af95-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7af95-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7af95-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7af95-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7af95-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af95-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7af95-114">See also</span></span>
- [<span data-ttu-id="7af95-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7af95-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7af95-116">AssemblyUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7af95-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
