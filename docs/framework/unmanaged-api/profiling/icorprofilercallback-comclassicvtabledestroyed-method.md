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
ms.openlocfilehash: f74e06ea4cb4d7a8eace8c7852f487bbdcbcd875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964632"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="105bc-102">ICorProfilerCallback::COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="105bc-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="105bc-103">通知分析工具, COM Interop 的 vtable 已終結。</span><span class="sxs-lookup"><span data-stu-id="105bc-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="105bc-104">此回呼可能永遠不會發生, 因為 vtable 的銷毀會非常接近關閉。</span><span class="sxs-lookup"><span data-stu-id="105bc-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105bc-105">語法</span><span class="sxs-lookup"><span data-stu-id="105bc-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="105bc-106">參數</span><span class="sxs-lookup"><span data-stu-id="105bc-106">Parameters</span></span>  
 `wrappedClassId`  
 <span data-ttu-id="105bc-107">在建立此 vtable 之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="105bc-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="105bc-108">在類別所實作為介面的識別碼。</span><span class="sxs-lookup"><span data-stu-id="105bc-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="105bc-109">如果介面僅供內部用, 這個值可能會是 Null。</span><span class="sxs-lookup"><span data-stu-id="105bc-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="105bc-110">在Vtable 開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="105bc-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="105bc-111">備註</span><span class="sxs-lookup"><span data-stu-id="105bc-111">Remarks</span></span>  
 <span data-ttu-id="105bc-112">分析工具不應在此方法的執行中封鎖, 因為堆疊可能不是處於允許垃圾收集的狀態, 因此無法啟用「搶先垃圾收集」。</span><span class="sxs-lookup"><span data-stu-id="105bc-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="105bc-113">如果分析工具在此處封鎖並嘗試垃圾收集, 執行時間將會封鎖, 直到這個回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="105bc-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="105bc-114">分析工具的此方法的執行不應呼叫 managed 程式碼, 或以任何方式進行, 以造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="105bc-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="105bc-115">需求</span><span class="sxs-lookup"><span data-stu-id="105bc-115">Requirements</span></span>  
 <span data-ttu-id="105bc-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="105bc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="105bc-117">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="105bc-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="105bc-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="105bc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="105bc-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="105bc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105bc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="105bc-120">See also</span></span>

- [<span data-ttu-id="105bc-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="105bc-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="105bc-122">COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="105bc-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
