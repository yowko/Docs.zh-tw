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
ms.openlocfilehash: c9e973009f46ef7e554ee2df63493464f4956342
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725478"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="6cd19-102">ICorProfilerCallback6::GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="6cd19-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>

<span data-ttu-id="6cd19-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="6cd19-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6cd19-104">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="6cd19-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd19-105">語法</span><span class="sxs-lookup"><span data-stu-id="6cd19-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cd19-106">參數</span><span class="sxs-lookup"><span data-stu-id="6cd19-106">Parameters</span></span>  

 `wszAssemblyPath`  
 <span data-ttu-id="6cd19-107">[in] 要修改其中繼資料之組件的路徑及名稱。</span><span class="sxs-lookup"><span data-stu-id="6cd19-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="6cd19-108">在 [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) 介面的位址指標，這個介面會指定要加入的元件參考。</span><span class="sxs-lookup"><span data-stu-id="6cd19-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cd19-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6cd19-109">Return Value</span></span>  

 <span data-ttu-id="6cd19-110">忽略此回呼傳回的值。</span><span class="sxs-lookup"><span data-stu-id="6cd19-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cd19-111">備註</span><span class="sxs-lookup"><span data-stu-id="6cd19-111">Remarks</span></span>  

 <span data-ttu-id="6cd19-112">此回呼是藉由在呼叫[ICorProfilerCallback5：： SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法時設定[COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md)事件遮罩旗標來控制。</span><span class="sxs-lookup"><span data-stu-id="6cd19-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="6cd19-113">如果 profiler 登錄 [ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 回呼方法，則執行時間會傳遞要載入之元件的路徑和名稱，以及指向該方法的 [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) 介面物件的指標。</span><span class="sxs-lookup"><span data-stu-id="6cd19-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="6cd19-114">然後，分析工具可以[ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) `COR_PRF_ASSEMBLY_REFERENCE_INFO` 針對其計畫從回呼中指定的元件參考的每個目標群組件，使用物件呼叫 ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference 方法 `GetAssemblyReferences` 。</span><span class="sxs-lookup"><span data-stu-id="6cd19-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="6cd19-115">若分析工具必須修改組件的中繼資料以加入組件參考時，才能使用 `GetAssemblyReferences` 回呼</span><span class="sxs-lookup"><span data-stu-id="6cd19-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="6cd19-116"> (但請注意，元件中繼資料的實際修改是在 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼方法中完成。 ) 分析工具應該執行 `GetAssemblyReferences` 回呼方法，以通知 common LANGUAGE runtime (CLR) 當載入模組時，將會新增元件參考。</span><span class="sxs-lookup"><span data-stu-id="6cd19-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="6cd19-117">這可以確保在這早期階段由 CLR 執行的組件共用決定，即使在分析工具計劃於稍後修改中繼資料組件參考時也能保持有效性。</span><span class="sxs-lookup"><span data-stu-id="6cd19-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="6cd19-118">這可以避免一些由分析工具中繼資料修改而導致 `SECURITY_E_INCOMPATIBLE_SHARE` 錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="6cd19-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="6cd19-119">分析工具會使用這個方法所提供的 [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) 物件，將元件參考加入至 CLR 元件參考關閉的寫入器。</span><span class="sxs-lookup"><span data-stu-id="6cd19-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="6cd19-120">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)物件只能從這個回呼內使用。</span><span class="sxs-lookup"><span data-stu-id="6cd19-120">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="6cd19-121">此回呼的 [ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) 方法呼叫不會產生修改過的中繼資料，而只會在修改過的元件參考關閉過程中。</span><span class="sxs-lookup"><span data-stu-id="6cd19-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="6cd19-122">分析工具仍然必須使用 [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) 物件，以明確地在參考元件的 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼中加入元件參考，即使它會執行 `GetAssemblyReferences` 回呼。</span><span class="sxs-lookup"><span data-stu-id="6cd19-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="6cd19-123">分析工具應該準備好接收相同元件的這個回呼的重複呼叫，而且每個這類重複呼叫的回應方式都相同 (藉由讓相同的 [ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) 呼叫集合) 。</span><span class="sxs-lookup"><span data-stu-id="6cd19-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd19-124">需求</span><span class="sxs-lookup"><span data-stu-id="6cd19-124">Requirements</span></span>  

 <span data-ttu-id="6cd19-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cd19-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd19-126">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6cd19-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6cd19-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cd19-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cd19-128">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd19-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd19-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cd19-129">See also</span></span>

- [<span data-ttu-id="6cd19-130">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="6cd19-130">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)
- [<span data-ttu-id="6cd19-131">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="6cd19-131">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="6cd19-132">COR_PRF_ASSEMBLY_REFERENCE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="6cd19-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="6cd19-133">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="6cd19-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
