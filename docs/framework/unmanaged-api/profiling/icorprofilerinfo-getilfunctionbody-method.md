---
title: ICorProfilerInfo::GetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: 8160bb5b9ca5e0a4e22a1a831e978eaf125e7605
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870488"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody 方法
從標頭開始，取得 Microsoft 中繼語言（MSIL）程式碼中方法主體的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 在函數所在模組的識別碼。  
  
 `methodId`  
 在方法的元資料標記。  
  
 `ppMethodHeader`  
 脫銷方法標頭的指標。  
  
 `pcbMethodSize`  
 脫銷指定方法大小的整數。  
  
## <a name="remarks"></a>備註  
 方法是由其所在的模組限定範圍。 由於 `GetILFunctionBody` 方法是設計用來在 common language runtime （CLR）載入 MSIL 程式碼之前，先對其授與工具的存取權，因此它會使用方法的元資料標記來尋找所需的實例。  
  
 如果 `methodId` 指向不含任何 MSIL 程式碼的方法（例如抽象方法或平台叫用（PInvoke）方法），則 `GetILFunctionBody` 可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
