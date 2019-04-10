---
title: ICorProfilerCallback::ModuleLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 354d2f278bcb0618b823b7300079278fc4c3315c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157341"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="7f9ce-102">ICorProfilerCallback::ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7f9ce-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="7f9ce-103">通知分析工具已完成載入的模組。</span><span class="sxs-lookup"><span data-stu-id="7f9ce-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f9ce-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f9ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f9ce-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7f9ce-106">[in]已完成載入的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="7f9ce-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7f9ce-107">[in]HRESULT，指出是否已成功載入的模組。</span><span class="sxs-lookup"><span data-stu-id="7f9ce-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f9ce-108">備註</span><span class="sxs-lookup"><span data-stu-id="7f9ce-108">Remarks</span></span>  
 <span data-ttu-id="7f9ce-109">值`moduleId`不是有效資訊要求直到`ModuleLoadFinished`呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="7f9ce-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="7f9ce-110">載入模組的某些部分可能會繼續之後`ModuleLoadFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="7f9ce-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="7f9ce-111">失敗 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="7f9ce-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="7f9ce-112">不過，成功的 HRESULT 中`hrStatus`僅會指示已成功載入模組的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="7f9ce-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f9ce-113">需求</span><span class="sxs-lookup"><span data-stu-id="7f9ce-113">Requirements</span></span>  
 <span data-ttu-id="7f9ce-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f9ce-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f9ce-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f9ce-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f9ce-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f9ce-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7f9ce-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7f9ce-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f9ce-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f9ce-118">See also</span></span>

- [<span data-ttu-id="7f9ce-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7f9ce-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7f9ce-120">ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="7f9ce-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
