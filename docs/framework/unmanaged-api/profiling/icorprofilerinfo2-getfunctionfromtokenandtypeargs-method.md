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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60a9ba78211cd02300cccc7d150bb08fa68b0604
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556177"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法
取得`FunctionID`函式使用指定的中繼資料語彙基元，包含類別，和`ClassID`值的任何型別引數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a>參數  
 `moduleID`  
 [in]函數所在之模組識別碼。  
  
 `funcDef`  
 [in]`mdMethodDef`參考函式的中繼資料語彙基元。  
  
 `classId`  
 [in]函式的包含類別的識別碼。  
  
 `cTypeArgs`  
 [in]指定的函式的型別參數的數目。 此值必須是零的非泛型函式。  
  
 `typeArgs`  
 [in]陣列`ClassID`每一個都是函式的引數的值。 值`typeArgs`可以是 NULL，如果`cTypeArgs`設為零。  
  
 `pFunctionID`  
 [out]指標`FunctionID`所指定函式。  
  
## <a name="remarks"></a>備註  
 呼叫`GetFunctionFromTokenAndTypeArgs`方法`mdMethodRef`中繼資料，而不是`mdMethodDef`中繼資料語彙基元可能會有無法預期的結果。 呼叫端應該解決`mdMethodRef`至`mdMethodDef`傳遞時。  
  
 如果尚未載入函式，呼叫`GetFunctionFromTokenAndTypeArgs`會導致發生，而這是危險的作業在許多內容中載入。 例如，在模組或類型載入期間呼叫這個方法可能會導致無限迴圈循環載入嘗試執行階段。  
  
 一般情況下，使用`GetFunctionFromTokenAndTypeArgs`建議您不要使用。 如果程式碼剖析工具有興趣的特定函式的事件，它們應該儲存`ModuleID`並`mdMethodDef`該函式，並使用[ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)若要檢查是否指定`FunctionID`是所需的函式。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
