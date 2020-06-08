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
ms.openlocfilehash: a33e51969dc0579d976f08470ebc6e2bcca04dd7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497162"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 方法
取得指定類別之開放式泛型定義的父模組和元資料標記、 `ClassID` 其父類別的，以及 `ClassID` 類別的每個類型引數的（如果有的話）。  
  
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
 脫銷指定類別之開放式泛型定義的父模組識別碼的指標。  
  
 `pTypeDefToken`  
 脫銷指定類別之開放式泛型定義的元資料標記的指標。  
  
 `pParentClassId`  
 [out] 父類別 ID 的指標。  
  
 `cNumTypeArgs`  
 [in] `typeArgs` 陣列的大小。  
  
 `pcNumTypeArgs`  
 [out] 可用的項目總數之指標。  
  
 `typeArgs`  
 [out] 一組 `ClassID` 值的陣列，其中每一項各代表此類別之型別引數的 ID。 方法傳回時， `typeArgs` 將包含部分或所有可用的 `ClassID` 值。  
  
## <a name="remarks"></a>備註  
 `GetClassIDInfo2`方法類似于[ICorProfilerInfo：： GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md)方法，但會取得 `GetClassIDInfo2` 泛型型別的其他資訊。  
  
 分析工具程式碼可以呼叫[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)來取得給定模組的[中繼資料](../metadata/index.md)介面。 然後，傳回至 `pTypeDefToken` 所參考位置的中繼資料語彙基元可以用來存取此類別的中繼資料。  
  
 `GetClassIDInfo2` 傳回之後，您必須確認 `typeArgs` 緩衝區夠大，以包含所有 `ClassID` 的值。 若要這樣做，請比對 `pcNumTypeArgs` 指向的值和 `cNumTypeArgs` 參數。 如果 `pcNumTypeArgs` 指向大於 `cNumTypeArgs` 的值，請配置較大的 `typeArgs` 緩衝區，並以較大的大小來更新 `cNumTypeArgs`，然後再次呼叫 `GetClassIDInfo2`。  
  
 或者，您也可以先使用長度為零的 `typeArgs` 緩衝區來呼叫 `GetClassIDInfo2`，以取得正確的緩衝區大小。 然後您可以設定 `typeArgs` 緩衝區大小為在 `pcNumTypeArgs` 中傳回的值，並且再呼叫 `GetClassIDInfo2` 一次。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
