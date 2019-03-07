---
title: ICorProfilerCallback6::GetAssemblyReferences 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a705257c150fe0272674c08c7b316ab968766cb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475329"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="9965d-102">ICorProfilerCallback6::GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="9965d-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>
<span data-ttu-id="9965d-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="9965d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9965d-104">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="9965d-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9965d-105">語法</span><span class="sxs-lookup"><span data-stu-id="9965d-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9965d-106">參數</span><span class="sxs-lookup"><span data-stu-id="9965d-106">Parameters</span></span>  
 `wszAssemblyPath`  
 <span data-ttu-id="9965d-107">[in] 要修改其中繼資料之組件的路徑及名稱。</span><span class="sxs-lookup"><span data-stu-id="9965d-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="9965d-108">[in]位址指標[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)參考加入指定的組件的介面。</span><span class="sxs-lookup"><span data-stu-id="9965d-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9965d-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9965d-109">Return Value</span></span>  
 <span data-ttu-id="9965d-110">忽略此回呼傳回的值。</span><span class="sxs-lookup"><span data-stu-id="9965d-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9965d-111">備註</span><span class="sxs-lookup"><span data-stu-id="9965d-111">Remarks</span></span>  
 <span data-ttu-id="9965d-112">此回呼由設定控制[ICORPROFILERCALLBACK5::SETEVENTMASK2](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)事件遮罩旗標時呼叫[ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="9965d-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="9965d-113">如果分析工具註冊[ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼方法，執行階段會傳遞要載入，以及一個指向組件的名稱與路徑[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)介面物件，該方法。</span><span class="sxs-lookup"><span data-stu-id="9965d-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="9965d-114">然後可以呼叫分析工具[icorprofilerassemblyreferenceprovider:: Addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)方法`COR_PRF_ASSEMBLY_REFERENCE_INFO`每個目標組件計劃要從指定的組件參考的物件`GetAssemblyReferences`回呼。</span><span class="sxs-lookup"><span data-stu-id="9965d-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="9965d-115">若分析工具必須修改組件的中繼資料以加入組件參考時，才能使用 `GetAssemblyReferences` 回呼</span><span class="sxs-lookup"><span data-stu-id="9965d-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="9965d-116">(不過請注意，組件的中繼資料的實際修改很[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼方法。)分析工具應在已載入模組時，實作 `GetAssemblyReferences` 回呼方法，以通知 Common Language Runtime (CLR) 將加入組件參考。</span><span class="sxs-lookup"><span data-stu-id="9965d-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="9965d-117">這可以確保在這早期階段由 CLR 執行的組件共用決定，即使在分析工具計劃於稍後修改中繼資料組件參考時也能保持有效性。</span><span class="sxs-lookup"><span data-stu-id="9965d-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="9965d-118">這可以避免一些由分析工具中繼資料修改而導致 `SECURITY_E_INCOMPATIBLE_SHARE` 錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="9965d-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="9965d-119">分析工具會使用[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)這個方法來加入組件參考 CLR 組件參考關閉查核器所提供的物件。</span><span class="sxs-lookup"><span data-stu-id="9965d-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="9965d-120">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)物件應該只會從用於此回呼。</span><span class="sxs-lookup"><span data-stu-id="9965d-120">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="9965d-121">若要呼叫[icorprofilerassemblyreferenceprovider:: Addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)從此回呼的方法不會造成已修改的中繼資料，但只有在已修改的組件參考關閉查核。</span><span class="sxs-lookup"><span data-stu-id="9965d-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="9965d-122">分析工具仍然必須使用[IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)明確加入從的 組件參考的物件[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼的參考組件，即使它會實作`GetAssemblyReferences`回呼。</span><span class="sxs-lookup"><span data-stu-id="9965d-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="9965d-123">分析工具應該已準備好接收此回呼中的重複呼叫相同的組件，以及應該如何回應相同的每個這類重複呼叫 (藉由一組相同[ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)呼叫)。</span><span class="sxs-lookup"><span data-stu-id="9965d-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9965d-124">需求</span><span class="sxs-lookup"><span data-stu-id="9965d-124">Requirements</span></span>  
 <span data-ttu-id="9965d-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9965d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9965d-126">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9965d-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9965d-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9965d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9965d-128">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9965d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9965d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9965d-129">See also</span></span>
- [<span data-ttu-id="9965d-130">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="9965d-130">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [<span data-ttu-id="9965d-131">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="9965d-131">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="9965d-132">COR_PRF_ASSEMBLY_REFERENCE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="9965d-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="9965d-133">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="9965d-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
