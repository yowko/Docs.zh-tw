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
ms.openlocfilehash: 62aad8339b34a4831211a45bd645906d73393d25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727142"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法

`ClassID`使用指定的元資料標記和 `ClassID` 任何類型引數的值，取得型別的。  
  
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
 在型別所在之模組的識別碼。  
  
 `typeDef`  
 在 `mdTypeDef` 參考該類型的元資料標記。  
  
 `cTypeArgs`  
 在給定類型的型別參數數目。 非泛型型別的這個值必須為零。  
  
 `typeArgs`  
 在值的陣列 `ClassID` ，每個值都是類型的引數。 如果設定為零，則的值 `typeArgs` 可以是 Null `cTypeArgs` 。  
  
 `pClassID`  
 擴展 `ClassID` 指定之類型的指標。  
  
## <a name="remarks"></a>備註  

 `GetClassFromTokenAndTypeArgs`使用 `mdTypeRef` 取代元資料標記來呼叫方法， `mdTypeDef` 可能會產生無法預測的結果; 呼叫端應該 `mdTypeRef` `mdTypeDef` 在傳遞時將解析為。  
  
 如果類型尚未載入，則呼叫 `GetClassFromTokenAndTypeArgs` 會觸發載入，這在許多內容中是危險的作業。 例如，在載入模組或其他類型期間呼叫這個方法，可能會導致無限迴圈，因為執行時間會嘗試迴圈載入專案。  
  
 一般情況下， `GetClassFromTokenAndTypeArgs` 不建議使用。 如果分析工具對特定類型的事件有興趣，則應該儲存該 `ModuleID` 類型的和 `mdTypeDef` ，並使用 [ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) 來檢查給定的是否 `ClassID` 為所需類型的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
