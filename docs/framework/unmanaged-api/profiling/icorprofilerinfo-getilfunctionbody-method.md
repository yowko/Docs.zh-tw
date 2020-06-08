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
ms.openlocfilehash: 5984c63f0e1a1859dd5cc2550d6dc37c963affb3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502999"
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
 方法是由其所在的模組限定範圍。 因為 `GetILFunctionBody` 方法是設計用來在 common language runtime （CLR）載入 MSIL 程式碼之前提供工具的存取權，所以它會使用方法的元資料標記來尋找所需的實例。  
  
 `GetILFunctionBody`如果 `methodId` 指向不含任何 MSIL 程式碼的方法（例如抽象方法或平台叫用（PInvoke）方法），則可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
