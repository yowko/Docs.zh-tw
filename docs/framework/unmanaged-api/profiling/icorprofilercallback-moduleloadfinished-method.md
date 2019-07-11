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
ms.openlocfilehash: c04b7862363b441ab35d6dd364c4dffaf7464153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769223"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="6abae-102">ICorProfilerCallback::ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="6abae-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="6abae-103">通知分析工具已完成載入的模組。</span><span class="sxs-lookup"><span data-stu-id="6abae-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6abae-104">語法</span><span class="sxs-lookup"><span data-stu-id="6abae-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6abae-105">參數</span><span class="sxs-lookup"><span data-stu-id="6abae-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="6abae-106">[in]已完成載入的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="6abae-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6abae-107">[in]HRESULT，指出是否已成功載入的模組。</span><span class="sxs-lookup"><span data-stu-id="6abae-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6abae-108">備註</span><span class="sxs-lookup"><span data-stu-id="6abae-108">Remarks</span></span>  
 <span data-ttu-id="6abae-109">值`moduleId`不是有效資訊要求直到`ModuleLoadFinished`呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="6abae-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="6abae-110">載入模組的某些部分可能會繼續之後`ModuleLoadFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="6abae-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="6abae-111">失敗 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="6abae-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6abae-112">不過，成功的 HRESULT 中`hrStatus`僅會指示已成功載入模組的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="6abae-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6abae-113">需求</span><span class="sxs-lookup"><span data-stu-id="6abae-113">Requirements</span></span>  
 <span data-ttu-id="6abae-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6abae-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6abae-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6abae-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6abae-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6abae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6abae-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6abae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6abae-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6abae-118">See also</span></span>

- [<span data-ttu-id="6abae-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6abae-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="6abae-120">ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="6abae-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
