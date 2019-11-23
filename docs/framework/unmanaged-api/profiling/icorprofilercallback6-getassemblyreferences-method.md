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
ms.openlocfilehash: d15f1b568c50cf4fca28966f94a6a4becf59e734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141634"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="b3f31-102">ICorProfilerCallback6::GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="b3f31-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>
<span data-ttu-id="b3f31-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="b3f31-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b3f31-104">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="b3f31-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f31-105">語法</span><span class="sxs-lookup"><span data-stu-id="b3f31-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3f31-106">參數</span><span class="sxs-lookup"><span data-stu-id="b3f31-106">Parameters</span></span>  
 `wszAssemblyPath`  
 <span data-ttu-id="b3f31-107">[in] 要修改其中繼資料之組件的路徑及名稱。</span><span class="sxs-lookup"><span data-stu-id="b3f31-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="b3f31-108">在[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)介面位址的指標，指定要加入的元件參考。</span><span class="sxs-lookup"><span data-stu-id="b3f31-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3f31-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b3f31-109">Return Value</span></span>  
 <span data-ttu-id="b3f31-110">忽略此回呼傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b3f31-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3f31-111">備註</span><span class="sxs-lookup"><span data-stu-id="b3f31-111">Remarks</span></span>  
 <span data-ttu-id="b3f31-112">呼叫[ICorProfilerCallback5：： SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法時，會設定[COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)事件遮罩旗標來控制此回呼。</span><span class="sxs-lookup"><span data-stu-id="b3f31-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="b3f31-113">如果分析工具註冊[ICorProfilerCallback6：： GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼方法，執行時間會傳遞要載入之元件的路徑和名稱，以及指向該方法的[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)介面物件指標。</span><span class="sxs-lookup"><span data-stu-id="b3f31-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="b3f31-114">然後，分析工具可以針對其計畫要從 `GetAssemblyReferences` 回呼中指定的元件參考的每個目標群組件，使用 `COR_PRF_ASSEMBLY_REFERENCE_INFO` 物件來呼叫[ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b3f31-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="b3f31-115">若分析工具必須修改組件的中繼資料以加入組件參考時，才能使用 `GetAssemblyReferences` 回呼</span><span class="sxs-lookup"><span data-stu-id="b3f31-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="b3f31-116">（但請注意，元件中繼資料的實際修改是在[ICorProfilerCallback：： ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼方法中完成）。分析工具應該會執行 `GetAssemblyReferences` 回呼方法，以通知 common language runtime （CLR）當模組載入時，將會加入元件參考。</span><span class="sxs-lookup"><span data-stu-id="b3f31-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="b3f31-117">這可以確保在這早期階段由 CLR 執行的組件共用決定，即使在分析工具計劃於稍後修改中繼資料組件參考時也能保持有效性。</span><span class="sxs-lookup"><span data-stu-id="b3f31-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="b3f31-118">這可以避免一些由分析工具中繼資料修改而導致 `SECURITY_E_INCOMPATIBLE_SHARE` 錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="b3f31-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="b3f31-119">分析工具會使用這個方法所提供的[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)物件，將元件參考加入至 CLR 元件參考結束的遍歷器。</span><span class="sxs-lookup"><span data-stu-id="b3f31-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="b3f31-120">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)物件只能在此回呼中使用。</span><span class="sxs-lookup"><span data-stu-id="b3f31-120">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="b3f31-121">呼叫此回呼中的[ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)方法，並不會產生修改過的中繼資料，而只會在已修改的元件參考關閉逐步解說中。</span><span class="sxs-lookup"><span data-stu-id="b3f31-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="b3f31-122">分析工具仍然必須使用[IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)物件，從參考元件的[ICorProfilerCallback：： ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼中明確新增元件參考，即使它會執行 `GetAssemblyReferences` 回呼也一樣。</span><span class="sxs-lookup"><span data-stu-id="b3f31-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="b3f31-123">分析工具應該準備好接收相同元件的此回呼的重複呼叫，而且每個這類重複呼叫的回應都是相同的（藉由建立相同的[ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)呼叫集合）。</span><span class="sxs-lookup"><span data-stu-id="b3f31-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f31-124">需求</span><span class="sxs-lookup"><span data-stu-id="b3f31-124">Requirements</span></span>  
 <span data-ttu-id="b3f31-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3f31-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3f31-126">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3f31-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3f31-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3f31-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3f31-128">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3f31-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f31-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3f31-129">See also</span></span>

- [<span data-ttu-id="b3f31-130">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="b3f31-130">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [<span data-ttu-id="b3f31-131">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="b3f31-131">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="b3f31-132">COR_PRF_ASSEMBLY_REFERENCE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="b3f31-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="b3f31-133">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="b3f31-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
