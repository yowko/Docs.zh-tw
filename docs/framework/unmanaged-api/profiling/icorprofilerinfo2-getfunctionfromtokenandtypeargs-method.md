---
title: "ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc89ca6213008192c0af8e519ae255c13e9763c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法
取得`FunctionID`函式，使用指定的中繼資料語彙基元，包含類別，來和`ClassID`值的任何型別引數。  
  
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
 [in]此函式所在模組的識別碼。  
  
 `funcDef`  
 [in]`mdMethodDef`參考函式的中繼資料語彙基元。  
  
 `classId`  
 [in]函式的包含類別的識別碼。  
  
 `cTypeArgs`  
 [in]指定函式的型別參數數目。 此值必須是零的非泛型函式。  
  
 `typeArgs`  
 [in]陣列`ClassID`值，其中每一個都是函式的引數。 值`typeArgs`可以是 NULL，如果`cTypeArgs`設為零。  
  
 `pFunctionID`  
 [out]指標`FunctionID`的指定函式。  
  
## <a name="remarks"></a>備註  
 呼叫`GetFunctionFromTokenAndTypeArgs`方法`mdMethodRef`中繼資料，而不是`mdMethodDef`中繼資料語彙基元可以有無法預期的結果。 呼叫端應該解決`mdMethodRef`至`mdMethodDef`時將傳遞給它。  
  
 如果尚未載入的函式，呼叫`GetFunctionFromTokenAndTypeArgs`會導致發生，這可能會有危險的作業，許多內容中載入。 比方說，在模組或型別載入期間呼叫這個方法可能會導致無限迴圈因為執行階段嘗試循環載入。  
  
 一般情況下，使用`GetFunctionFromTokenAndTypeArgs`不建議使用。 如果分析工具想要的特定函式的事件中，它們應該儲存`ModuleID`和`mdMethodDef`該函式，然後使用[icorprofilerinfo2:: Getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)來檢查是否指定`FunctionID`是所需的函式。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
