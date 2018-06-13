---
title: ICorProfilerInfo::GetAssemblyInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3579020ce268cd59a091e685fae2e97b3191c55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456119"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>ICorProfilerInfo::GetAssemblyInfo 方法
接受組件識別碼，並傳回組件的名稱及其資訊清單模組的識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a>參數  
 `assemblyId`  
 [in] 組件的識別項。  
  
 `cchName`  
 [in] `szName` 的長度 (以字元為單位)。  
  
 `pcchName`  
 [out] 組件名稱總字元長度的指標。  
  
 `szName`  
 [out] 呼叫端提供的寬字元緩衝區。 函式傳回時，會包含組件的名稱。  
  
 `pAppDomainId`  
 [out] 包含組件之應用程式定義域的識別碼指標。  
  
 `pModuleId`  
 [out] 組件資訊清單模組的識別碼指標。  
  
## <a name="remarks"></a>備註  
 在此方法傳回之後，您必須確認 `szName` 緩衝區的大小足以包含組件的完整檔案名稱。 若要執行這項作業，請比較 `pcchName` 指向的值和 `cchName` 參數的值。 如果 `pcchName` 指向大於 `cchName` 的值，請配置較大的 `szName` 緩衝區，並以較大的大小來更新 `cchName`，然後再次呼叫 `GetAssemblyInfo`。  
  
 或者，您也可以先使用長度為零的 `szName` 緩衝區來呼叫 `GetAssemblyInfo`，以取得正確的緩衝區大小。 接著您就可以依據 `pcchName` 中傳回的值來調整緩衝區大小，並再次呼叫 `GetAssemblyInfo`。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
