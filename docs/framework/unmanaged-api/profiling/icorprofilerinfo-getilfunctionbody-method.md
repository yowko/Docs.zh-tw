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
ms.openlocfilehash: 337c4fd091ebf7c39f7eee2358ca4f4df239cce3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687524"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody 方法

從標頭開始，取得 Microsoft 中繼語言 (MSIL 的方法主體指標) 程式碼。  
  
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
 在函數所在之模組的識別碼。  
  
 `methodId`  
 在方法的元資料標記。  
  
 `ppMethodHeader`  
 擴展方法標頭的指標。  
  
 `pcbMethodSize`  
 擴展指定方法大小的整數。  
  
## <a name="remarks"></a>備註  

 方法的範圍是它所在的模組。 因為 `GetILFunctionBody` 方法是設計為在 common language runtime (CLR) 載入 MSIL 程式碼之前，提供工具的存取權，所以它會使用方法的中繼資料 token 來尋找所需的實例。  
  
 `GetILFunctionBody` 如果 `methodId` 指向沒有任何 MSIL 程式碼 (的方法（例如抽象方法），或平台叫用 (PInvoke) 方法) ，則可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
