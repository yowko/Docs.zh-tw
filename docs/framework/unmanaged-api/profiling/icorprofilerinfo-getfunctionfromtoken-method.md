---
title: ICorProfilerInfo::GetFunctionFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb894e3f52d28ce419ddda90f9fc0ac0e8dce022
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a>ICorProfilerInfo::GetFunctionFromToken 方法
取得函式的識別碼。 這個方法是.NET Framework 2.0 版中已過時。 使用[icorprofilerinfo2:: Getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a>備註  
 `GetFunctionFromToken`方法不適用於泛型函式或函式中的泛型型別; 現在已過時。 使用`ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`的所有函式。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1、 1.0  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
