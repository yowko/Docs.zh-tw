---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: e0663ff122397ba639a0a219e513be2f3f0cbbef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862759"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法
使用指定的元資料標記和任何類型引數的 `ClassID` 值，取得類型的 `ClassID`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>參數  
 `moduleID`  
 在類型所在之模組的識別碼。  
  
 `typeDef`  
 在參考型別的 `mdTypeDef` 中繼資料 token。  
  
 `cTypeArgs`  
 在給定類型的類型參數數目。 非泛型型別的這個值必須是零。  
  
 `typeArgs`  
 在`ClassID` 值的陣列，其中每一個都是類型的引數。 如果 `cTypeArgs` 設定為零，`typeArgs` 的值可以是 Null。  
  
 `pClassID`  
 脫銷指定類型之 `ClassID` 的指標。  
  
## <a name="remarks"></a>備註  
 使用 `mdTypeRef` 而不是 `mdTypeDef` 元資料標記呼叫 `GetClassFromTokenAndTypeArgs` 方法，可能會產生無法預期的結果;呼叫端應該在傳遞時，將 `mdTypeRef` 解析成 `mdTypeDef`。  
  
 如果尚未載入類型，呼叫 `GetClassFromTokenAndTypeArgs` 將會觸發載入，這在許多內容中是危險的作業。 例如，在載入模組或其他類型期間呼叫這個方法，可能會導致無限迴圈，因為執行時間會嘗試迴圈載入專案。  
  
 一般而言，不建議使用 `GetClassFromTokenAndTypeArgs`。 如果分析工具對特定類型的事件有興趣，則應該儲存該類型的 `ModuleID` 和 `mdTypeDef`，並使用[ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)來檢查給定的 `ClassID` 是否為所需類型的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
