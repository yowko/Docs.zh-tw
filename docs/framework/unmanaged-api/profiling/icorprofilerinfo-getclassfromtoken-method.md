---
title: ICorProfilerInfo::GetClassFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 841953625235406f013e9f140ad91c7b65680e47
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863949"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a>ICorProfilerInfo::GetClassFromToken 方法
取得指定元資料標記之類別的識別碼。 這個方法在 .NET Framework 版本2.0 中已過時。 請改用[ICorProfilerInfo2：： GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a>參數  
 `moduleID`  
 在包含類別之模組的識別碼。  
  
 `typeDef`  
 在參考類別的 `mdTypeDef` 中繼資料 token。  
  
 `cTypeArgs`  
 脫銷類別識別碼的指標。  
  
## <a name="remarks"></a>備註  
 這個方法已過時;請改用適用于所有類型的 `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.0、1.1  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
