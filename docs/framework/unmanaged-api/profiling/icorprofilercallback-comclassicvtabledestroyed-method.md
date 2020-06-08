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
ms.openlocfilehash: 708981155589d491a3b1819adb611a28072dd1bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500311"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="d93ea-102">ICorProfilerCallback::COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="d93ea-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="d93ea-103">通知分析工具，COM Interop 的 vtable 已終結。</span><span class="sxs-lookup"><span data-stu-id="d93ea-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d93ea-104">此回呼可能永遠不會發生，因為 vtable 的銷毀會非常接近關閉。</span><span class="sxs-lookup"><span data-stu-id="d93ea-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d93ea-105">語法</span><span class="sxs-lookup"><span data-stu-id="d93ea-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d93ea-106">參數</span><span class="sxs-lookup"><span data-stu-id="d93ea-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="d93ea-107">\[in] 中建立此 vtable 的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="d93ea-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="d93ea-108">\[in] 類別所實作為介面的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d93ea-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="d93ea-109">如果介面僅供內部用，這個值可能會是 Null。</span><span class="sxs-lookup"><span data-stu-id="d93ea-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="d93ea-110">\[in] vtable 開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="d93ea-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="d93ea-111">備註</span><span class="sxs-lookup"><span data-stu-id="d93ea-111">Remarks</span></span>  
 <span data-ttu-id="d93ea-112">分析工具不應在此方法的執行中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用「搶先垃圾收集」。</span><span class="sxs-lookup"><span data-stu-id="d93ea-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="d93ea-113">如果分析工具在此處封鎖並嘗試垃圾收集，執行時間將會封鎖，直到這個回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="d93ea-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="d93ea-114">分析工具的此方法的執行不應呼叫 managed 程式碼，或以任何方式進行，以造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="d93ea-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d93ea-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="d93ea-115">Requirements</span></span>  
 <span data-ttu-id="d93ea-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d93ea-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d93ea-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d93ea-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d93ea-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d93ea-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d93ea-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d93ea-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93ea-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d93ea-120">See also</span></span>

- [<span data-ttu-id="d93ea-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d93ea-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d93ea-122">COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="d93ea-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
