---
title: "ICorProfilerCallback::COMClassicVTableDestroyed 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebff8297a708b130a0d3983fd75b76c3aeaeceaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="b0ae5-102">ICorProfilerCallback::COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="b0ae5-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="b0ae5-103">通知分析工具 COM interop 的 vtable 正在被終結。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0ae5-104">因為發生 vtable 的解構非常接近關機，很可能永遠不會發生，此回呼。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ae5-105">語法</span><span class="sxs-lookup"><span data-stu-id="b0ae5-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0ae5-106">參數</span><span class="sxs-lookup"><span data-stu-id="b0ae5-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="b0ae5-107">[in]為其建立此 vtable 的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="b0ae5-108">[in]此類別所實作的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="b0ae5-109">如果只是內部介面，這個值可能是 NULL。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="b0ae5-110">[in]開始在 vtable 的指標。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0ae5-111">備註</span><span class="sxs-lookup"><span data-stu-id="b0ae5-111">Remarks</span></span>  
 <span data-ttu-id="b0ae5-112">因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個方法實作封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b0ae5-113">如果分析工具會封鎖這裡並嘗試執行記憶體回收、 執行階段將會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b0ae5-114">Managed 程式碼或任何方式原因 managed 記憶體配置中，不應該呼叫這個方法的程式碼剖析工具實作。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ae5-115">需求</span><span class="sxs-lookup"><span data-stu-id="b0ae5-115">Requirements</span></span>  
 <span data-ttu-id="b0ae5-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0ae5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ae5-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0ae5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0ae5-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0ae5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0ae5-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ae5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ae5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0ae5-120">See Also</span></span>  
 [<span data-ttu-id="b0ae5-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b0ae5-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b0ae5-122">COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="b0ae5-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
