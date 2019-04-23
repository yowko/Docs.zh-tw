---
title: ICorProfilerCallback::COMClassicVTableCreated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4aa11b036c64ff6ffeec583c4cdd818d26067a74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162445"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="cb90d-102">ICorProfilerCallback::COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="cb90d-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="cb90d-103">通知分析工具已建立的 COM interop 的 vtable，所指定的 IID 和類別。</span><span class="sxs-lookup"><span data-stu-id="cb90d-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb90d-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb90d-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb90d-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb90d-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="cb90d-106">[in]已建立 vtable 類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb90d-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="cb90d-107">[in]此類別所實作的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb90d-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="cb90d-108">如果介面僅供內部，這個值可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="cb90d-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="cb90d-109">[in]Vtable 開頭指標。</span><span class="sxs-lookup"><span data-stu-id="cb90d-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="cb90d-110">[in]Vtable 中的位置數目。</span><span class="sxs-lookup"><span data-stu-id="cb90d-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb90d-111">備註</span><span class="sxs-lookup"><span data-stu-id="cb90d-111">Remarks</span></span>  
 <span data-ttu-id="cb90d-112">因為堆疊可能無法在狀態，讓記憶體回收，分析工具不應在實作這個方法封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="cb90d-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="cb90d-113">如果分析工具會封鎖這裡並嘗試進行記憶體回收、 執行階段將會封鎖，直到此回呼中傳回。</span><span class="sxs-lookup"><span data-stu-id="cb90d-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="cb90d-114">Managed 程式碼，或以任何方式造成 managed 記憶體配置，不應該呼叫這個方法的程式碼剖析工具的實作。</span><span class="sxs-lookup"><span data-stu-id="cb90d-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb90d-115">需求</span><span class="sxs-lookup"><span data-stu-id="cb90d-115">Requirements</span></span>  
 <span data-ttu-id="cb90d-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb90d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb90d-117">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb90d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb90d-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb90d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb90d-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb90d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb90d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb90d-120">See also</span></span>

- [<span data-ttu-id="cb90d-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cb90d-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cb90d-122">COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="cb90d-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
