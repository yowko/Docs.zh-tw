---
title: "ICorProfilerCallback::COMClassicVTableCreated 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39fa655065c2af10750b1285ef047678874723ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="248ed-102">ICorProfilerCallback::COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="248ed-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="248ed-103">通知分析工具已經建立的 COM interop vtable 指定 IID 和類別。</span><span class="sxs-lookup"><span data-stu-id="248ed-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="248ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="248ed-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="248ed-105">參數</span><span class="sxs-lookup"><span data-stu-id="248ed-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="248ed-106">[in]已建立在 vtable 的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="248ed-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="248ed-107">[in]此類別所實作的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="248ed-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="248ed-108">如果只是內部介面，這個值可能是 NULL。</span><span class="sxs-lookup"><span data-stu-id="248ed-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="248ed-109">[in]開始在 vtable 的指標。</span><span class="sxs-lookup"><span data-stu-id="248ed-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="248ed-110">[in]會在 vtable 中的插槽數目。</span><span class="sxs-lookup"><span data-stu-id="248ed-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="248ed-111">備註</span><span class="sxs-lookup"><span data-stu-id="248ed-111">Remarks</span></span>  
 <span data-ttu-id="248ed-112">因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個方法實作封鎖，因此無法啟用先佔式記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="248ed-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="248ed-113">如果分析工具會封鎖這裡並嘗試執行記憶體回收、 執行階段將會封鎖此回呼傳回之前。</span><span class="sxs-lookup"><span data-stu-id="248ed-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="248ed-114">Managed 程式碼或任何方式原因 managed 記憶體配置中，不應該呼叫這個方法的程式碼剖析工具實作。</span><span class="sxs-lookup"><span data-stu-id="248ed-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="248ed-115">需求</span><span class="sxs-lookup"><span data-stu-id="248ed-115">Requirements</span></span>  
 <span data-ttu-id="248ed-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="248ed-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="248ed-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="248ed-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="248ed-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="248ed-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="248ed-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="248ed-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248ed-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="248ed-120">See Also</span></span>  
 [<span data-ttu-id="248ed-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="248ed-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="248ed-122">COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="248ed-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
