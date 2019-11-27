---
title: ICorProfilerInfo::GetFunctionInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: 0a3ec1a317fbeba2bf792378663e2fe940a8ec10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439110"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>ICorProfilerInfo::GetFunctionInfo 方法
取得所指定函式的父類別和元資料標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 在要取得其父類別和元資料標記的函式識別碼。  
  
 `pClassId`  
 [out] 函式父類別的指標。  
  
 `pModuleId`  
 [out] 定義函式父類別的模組指標。  
  
 `pToken`  
 [out] 此函式中繼資料語彙基元的指標。  
  
## <a name="remarks"></a>備註  
 分析工具程式碼可以呼叫[ICorProfilerInfo：： GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)來取得給定模組的中繼資料介面。 然後，傳回至 `pToken` 所參考位置的中繼資料語彙基元可以用來存取此函式的中繼資料。  
  
 如需使用函式的詳細資訊，可能無法在泛型類別上取得函數的 `ClassID`。 在此情況下，`pClassId` 將會是0。 Profiler 程式碼應該使用[ICorProfilerInfo2：： GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)搭配 COR_PRF_FRAME_INFO 值，以提供更多內容。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
