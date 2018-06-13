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
ms.openlocfilehash: 2c30fb5d5576a7bed403f48504ead923df212de9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450371"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="36d54-102">ICorProfilerCallback::ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="36d54-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="36d54-103">通知分析工具正在卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="36d54-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d54-104">語法</span><span class="sxs-lookup"><span data-stu-id="36d54-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36d54-105">參數</span><span class="sxs-lookup"><span data-stu-id="36d54-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="36d54-106">[in]識別正在卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="36d54-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36d54-107">備註</span><span class="sxs-lookup"><span data-stu-id="36d54-107">Remarks</span></span>  
 <span data-ttu-id="36d54-108">值`classId`不正確資訊要求之後`ClassUnloadStarted`方法會傳回-這是程式碼剖析工具來取得這個類別相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="36d54-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d54-109">需求</span><span class="sxs-lookup"><span data-stu-id="36d54-109">Requirements</span></span>  
 <span data-ttu-id="36d54-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36d54-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d54-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36d54-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36d54-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36d54-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36d54-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d54-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d54-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36d54-114">See Also</span></span>  
 [<span data-ttu-id="36d54-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="36d54-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="36d54-116">ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="36d54-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
