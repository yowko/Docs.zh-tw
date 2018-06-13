---
title: ICorProfilerCallback::COMClassicVTableDestroyed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30d1e80d05344448c19c9f8f2d261442e4041487
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451713"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="3487f-102">ICorProfilerCallback::COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="3487f-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="3487f-103">通知分析工具 COM interop 的 vtable 正在被終結。</span><span class="sxs-lookup"><span data-stu-id="3487f-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3487f-104">因為發生 vtable 的解構非常接近關機，很可能永遠不會發生，此回呼。</span><span class="sxs-lookup"><span data-stu-id="3487f-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3487f-105">語法</span><span class="sxs-lookup"><span data-stu-id="3487f-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3487f-106">參數</span><span class="sxs-lookup"><span data-stu-id="3487f-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="3487f-107">[in]為其建立此 vtable 的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="3487f-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="3487f-108">[in]此類別所實作的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="3487f-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="3487f-109">如果只是內部介面，這個值可能是 NULL。</span><span class="sxs-lookup"><span data-stu-id="3487f-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="3487f-110">[in]開始在 vtable 的指標。</span><span class="sxs-lookup"><span data-stu-id="3487f-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3487f-111">備註</span><span class="sxs-lookup"><span data-stu-id="3487f-111">Remarks</span></span>  
 <span data-ttu-id="3487f-112">因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個方法實作封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="3487f-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3487f-113">如果分析工具會封鎖這裡並嘗試執行記憶體回收、 執行階段將會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="3487f-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3487f-114">Managed 程式碼或任何方式原因 managed 記憶體配置中，不應該呼叫這個方法的程式碼剖析工具實作。</span><span class="sxs-lookup"><span data-stu-id="3487f-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3487f-115">需求</span><span class="sxs-lookup"><span data-stu-id="3487f-115">Requirements</span></span>  
 <span data-ttu-id="3487f-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3487f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3487f-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3487f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3487f-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3487f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3487f-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3487f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3487f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3487f-120">See Also</span></span>  
 [<span data-ttu-id="3487f-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3487f-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3487f-122">COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="3487f-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
