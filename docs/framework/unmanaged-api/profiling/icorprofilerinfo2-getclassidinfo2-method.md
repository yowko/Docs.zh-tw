---
title: ICorProfilerInfo2::GetClassIDInfo2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: 8ce02b8b44074bed2da9e302f95a67a528601bf8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433434"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 方法
Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>參數  
 `classId`  
 [in] 要擷取資訊的類別 ID。  
  
 `pModuleId`  
 [out] Pointer to the ID of the parent module for the open generic definition of the specified class.  
  
 `pTypeDefToken`  
 [out] Pointer to the metadata token for the open generic definition of the specified class.  
  
 `pParentClassId`  
 [out] 父類別 ID 的指標。  
  
 `cNumTypeArgs`  
 [in] `typeArgs` 陣列的大小。  
  
 `pcNumTypeArgs`  
 [out] 可用的項目總數之指標。  
  
 `typeArgs`  
 [out] 一組 `ClassID` 值的陣列，其中每一項各代表此類別之型別引數的 ID。 方法傳回時， `typeArgs` 將包含部分或所有可用的 `ClassID` 值。  
  
## <a name="remarks"></a>備註  
 The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.  
  
 The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module. 然後，傳回至 `pTypeDefToken` 所參考位置的中繼資料語彙基元可以用來存取此類別的中繼資料。  
  
 `GetClassIDInfo2` 傳回之後，您必須確認 `typeArgs` 緩衝區夠大，以包含所有 `ClassID` 的值。 若要這樣做，請比對 `pcNumTypeArgs` 指向的值和 `cNumTypeArgs` 參數。 如果 `pcNumTypeArgs` 指向大於 `cNumTypeArgs` 的值，請配置較大的 `typeArgs` 緩衝區，並以較大的大小來更新 `cNumTypeArgs`，然後再次呼叫 `GetClassIDInfo2`。  
  
 或者，您也可以先使用長度為零的 `typeArgs` 緩衝區來呼叫 `GetClassIDInfo2`，以取得正確的緩衝區大小。 然後您可以設定 `typeArgs` 緩衝區大小為在 `pcNumTypeArgs` 中傳回的值，並且再呼叫 `GetClassIDInfo2` 一次。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
