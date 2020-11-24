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
ms.openlocfilehash: 5a29507ca56cac4ab800845e3a88706dc7a25379
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683988"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="ce1a8-102">ICorProfilerCallback::ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="ce1a8-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>

<span data-ttu-id="ce1a8-103">通知分析工具模組已完成載入。</span><span class="sxs-lookup"><span data-stu-id="ce1a8-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce1a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce1a8-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce1a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce1a8-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="ce1a8-106">在已完成載入之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce1a8-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ce1a8-107">在HRESULT，指出模組是否已成功載入。</span><span class="sxs-lookup"><span data-stu-id="ce1a8-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce1a8-108">備註</span><span class="sxs-lookup"><span data-stu-id="ce1a8-108">Remarks</span></span>  

 <span data-ttu-id="ce1a8-109">在呼叫方法之前，的值對 `moduleId` 資訊要求而言是不正確 `ModuleLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="ce1a8-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="ce1a8-110">載入模組的某些部分可能會在回呼之後繼續進行 `ModuleLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="ce1a8-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="ce1a8-111">中的失敗 HRESULT `hrStatus` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="ce1a8-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ce1a8-112">但是，中的成功 HRESULT `hrStatus` 只會指出載入模組的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="ce1a8-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce1a8-113">需求</span><span class="sxs-lookup"><span data-stu-id="ce1a8-113">Requirements</span></span>  

 <span data-ttu-id="ce1a8-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1a8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce1a8-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce1a8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce1a8-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce1a8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce1a8-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce1a8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce1a8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce1a8-118">See also</span></span>

- [<span data-ttu-id="ce1a8-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ce1a8-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ce1a8-120">ModuleLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="ce1a8-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
