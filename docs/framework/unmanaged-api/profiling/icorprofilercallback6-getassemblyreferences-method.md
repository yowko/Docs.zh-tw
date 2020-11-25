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
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences 方法

[.NET Framework 4.5.2 與更新版本提供支援]  
  
 當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>參數  

 `wszAssemblyPath`  
 [in] 要修改其中繼資料之組件的路徑及名稱。  
  
 `pAsmRefProvider`  
 在 [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) 介面的位址指標，這個介面會指定要加入的元件參考。  
  
## <a name="return-value"></a>傳回值  

 忽略此回呼傳回的值。  
  
## <a name="remarks"></a>備註  

 此回呼是藉由在呼叫[ICorProfilerCallback5：： SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法時設定[COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md)事件遮罩旗標來控制。 如果 profiler 登錄 [ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 回呼方法，則執行時間會傳遞要載入之元件的路徑和名稱，以及指向該方法的 [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) 介面物件的指標。 然後，分析工具可以[ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) `COR_PRF_ASSEMBLY_REFERENCE_INFO` 針對其計畫從回呼中指定的元件參考的每個目標群組件，使用物件呼叫 ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference 方法 `GetAssemblyReferences` 。  
  
 若分析工具必須修改組件的中繼資料以加入組件參考時，才能使用 `GetAssemblyReferences` 回呼  (但請注意，元件中繼資料的實際修改是在 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼方法中完成。 ) 分析工具應該執行 `GetAssemblyReferences` 回呼方法，以通知 common LANGUAGE runtime (CLR) 當載入模組時，將會新增元件參考。  這可以確保在這早期階段由 CLR 執行的組件共用決定，即使在分析工具計劃於稍後修改中繼資料組件參考時也能保持有效性。  這可以避免一些由分析工具中繼資料修改而導致 `SECURITY_E_INCOMPATIBLE_SHARE` 錯誤的情況。  
  
 分析工具會使用這個方法所提供的 [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) 物件，將元件參考加入至 CLR 元件參考關閉的寫入器。  [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)物件只能從這個回呼內使用。 此回呼的 [ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) 方法呼叫不會產生修改過的中繼資料，而只會在修改過的元件參考關閉過程中。 分析工具仍然必須使用 [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) 物件，以明確地在參考元件的 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼中加入元件參考，即使它會執行 `GetAssemblyReferences` 回呼。  
  
 分析工具應該準備好接收相同元件的這個回呼的重複呼叫，而且每個這類重複呼叫的回應方式都相同 (藉由讓相同的 [ICorProfilerAssemblyReferenceProvider：： AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) 呼叫集合) 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback6 介面](icorprofilercallback6-interface.md)
- [ModuleLoadFinished 方法](icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO 結構](cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider 介面](icorprofilerassemblyreferenceprovider-interface.md)
