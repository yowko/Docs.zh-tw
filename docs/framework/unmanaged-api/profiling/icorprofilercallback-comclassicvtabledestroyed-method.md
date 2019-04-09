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
ms.openlocfilehash: 63dc9ee81c98a23f01948a142018369eca7210b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116751"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="4dc29-102">ICorProfilerCallback::COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="4dc29-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="4dc29-103">通知分析工具 COM interop 的 vtable 正在被終結。</span><span class="sxs-lookup"><span data-stu-id="4dc29-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc29-104">此回呼是可能永遠不會發生，，因為發生 vtable 的解構非常接近關機。</span><span class="sxs-lookup"><span data-stu-id="4dc29-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc29-105">語法</span><span class="sxs-lookup"><span data-stu-id="4dc29-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dc29-106">參數</span><span class="sxs-lookup"><span data-stu-id="4dc29-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="4dc29-107">[in]為其建立此 vtable 類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4dc29-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="4dc29-108">[in]此類別所實作的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="4dc29-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="4dc29-109">如果介面僅供內部，這個值可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="4dc29-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="4dc29-110">[in]Vtable 開頭指標。</span><span class="sxs-lookup"><span data-stu-id="4dc29-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dc29-111">備註</span><span class="sxs-lookup"><span data-stu-id="4dc29-111">Remarks</span></span>  
 <span data-ttu-id="4dc29-112">因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在實作這個方法封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="4dc29-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="4dc29-113">如果分析工具會封鎖這裡並嘗試進行記憶體回收、 執行階段將會封鎖，直到此回呼中傳回。</span><span class="sxs-lookup"><span data-stu-id="4dc29-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="4dc29-114">Managed 程式碼，或以任何方式造成 managed 記憶體配置，不應該呼叫這個方法的程式碼剖析工具的實作。</span><span class="sxs-lookup"><span data-stu-id="4dc29-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dc29-115">需求</span><span class="sxs-lookup"><span data-stu-id="4dc29-115">Requirements</span></span>  
 <span data-ttu-id="4dc29-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc29-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dc29-117">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4dc29-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4dc29-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dc29-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4dc29-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="4dc29-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4dc29-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dc29-120">See also</span></span>

- [<span data-ttu-id="4dc29-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4dc29-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="4dc29-122">COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="4dc29-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
