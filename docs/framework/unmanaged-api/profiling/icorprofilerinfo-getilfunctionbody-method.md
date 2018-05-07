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
ms.openlocfilehash: bde194023ff6913db9a56e30eddaad8d7abc5ad1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody 方法
取得 Microsoft intermediate language (MSIL) 程式碼中，開始標頭在方法主體的指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a>參數  
 `moduleId`  
 [in]此函式所在模組的識別碼。  
  
 `methodId`  
 [in]方法的中繼資料語彙基元。  
  
 `ppMethodHeader`  
 [out]方法的標頭的指標。  
  
 `pcbMethodSize`  
 [out]整數，指定方法的大小。  
  
## <a name="remarks"></a>備註  
 方法的範圍是由其所在的模組。 因為`GetILFunctionBody`方法設計用來讓工具可以存取的 MSIL 程式碼之前已載入 common language runtime (CLR)，它使用的中繼資料語彙基元的方法來尋找所需的執行個體。  
  
 `GetILFunctionBody` 如果可以傳回 CORPROF_E_FUNCTION_NOT_IL HRESULT`methodId`指向方法沒有任何 MSIL 程式碼 （例如，一個抽象方法或平台叫用 (PInvoke) 方法）。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
