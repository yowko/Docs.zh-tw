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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 484fb5b8398e3ebd61d1c300afec1536ee1dc0c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780605"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody 方法
Microsoft intermediate language (MSIL) 程式碼，開始標頭中取得方法主體的指標。  
  
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
 [in]函數所在之模組識別碼。  
  
 `methodId`  
 [in]方法的中繼資料語彙基元。  
  
 `ppMethodHeader`  
 [out]方法的標頭指標。  
  
 `pcbMethodSize`  
 [out]整數，指定方法的大小。  
  
## <a name="remarks"></a>備註  
 方法的範圍是由其所在的模組。 因為`GetILFunctionBody`方法設計用來讓 MSIL 程式碼的工具存取之前已經將它載入 common language runtime (CLR)，它使用的中繼資料語彙基元的方法來尋找所需的執行個體。  
  
 `GetILFunctionBody` 如果可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT`methodId`指向一個方法，沒有任何 MSIL 程式碼 （例如抽象方法或平台叫用 (PInvoke) 方法）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
