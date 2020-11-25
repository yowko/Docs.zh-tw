---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
ms.openlocfilehash: 17a6220598010c0bee9c3f0485860aa0b2dc5f3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727103"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法

`FunctionID`使用指定的元資料標記、包含類別以及 `ClassID` 任何類型引數的值，取得函數的。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a>參數  

 `moduleID`  
 在函數所在之模組的識別碼。  
  
 `funcDef`  
 在 `mdMethodDef` 參考函數的元資料標記。  
  
 `classId`  
 在函數包含類別的識別碼。  
  
 `cTypeArgs`  
 在指定函式的型別參數數目。 非泛型函數的這個值必須為零。  
  
 `typeArgs`  
 在值的陣列 `ClassID` ，每個值都是函數的引數。 如果設定為零，則的值 `typeArgs` 可以是 Null `cTypeArgs` 。  
  
 `pFunctionID`  
 擴展指定之函式的指標 `FunctionID` 。  
  
## <a name="remarks"></a>備註  

 `GetFunctionFromTokenAndTypeArgs`使用 `mdMethodRef` 中繼資料來呼叫方法，而不是使用 `mdMethodDef` 元資料標記，可能會產生無法預測的結果。 當呼叫端傳遞時，呼叫端應該將解析 `mdMethodRef` 為 `mdMethodDef` 。  
  
 如果尚未載入此函式，呼叫 `GetFunctionFromTokenAndTypeArgs` 會導致載入發生，這在許多內容中是危險的作業。 例如，在載入模組或類型期間呼叫這個方法，可能會導致無限迴圈，因為執行時間會嘗試迴圈載入專案。  
  
 一般情況下， `GetFunctionFromTokenAndTypeArgs` 不建議使用。 如果分析工具對特定函式的事件有興趣，則應該儲存該函式的 `ModuleID` 和 `mdMethodDef` ，並使用 [ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) 檢查給定的是否為所需函式的 `FunctionID` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
