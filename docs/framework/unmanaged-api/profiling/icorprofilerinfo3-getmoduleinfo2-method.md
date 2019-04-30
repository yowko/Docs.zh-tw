---
title: ICorProfilerInfo3::GetModuleInfo2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fadca931ca4a57c83257f24e34e847870c9f493
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040959"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 方法
提供模組 ID，傳回該模組的檔案名稱、此模組父代組件的 ID 和描述模組屬性的位元遮罩。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 [in] 將被擷取資訊的模組 ID。  
  
 `ppBaseLoadAddress`  
 [out] 載入模組的基底位址。  
  
 `cchName`  
 [in] `szName` 傳回緩衝區的長度 (以字元為單位)。  
  
 `pcchName`  
 [out] 所傳回的模組檔案名稱之總字元長度的指標。  
  
 `szName`  
 [out] 呼叫端提供的寬字元緩衝區。 當方法傳回時，這個緩衝區會包含模組的檔案名稱。  
  
 `pAssemblyId`  
 [out] 模組父組件之 ID 的指標。  
  
 `pdwModuleFlags`  
 [out]從值的位元遮罩[COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)列舉，指定了模組的屬性。  
  
## <a name="remarks"></a>備註  
 若為動態模組，則 `szName` 參數為模組之中繼資料名稱，且基底位址為 0 (零)。 中繼資料名稱是中繼資料內的模組資料表之「名稱」欄中的值。 這也會公開成<xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType>屬性，managed 程式碼，以及`szName`的參數[imetadataimport:: Getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) unmanaged 中繼資料的用戶端程式碼的方法。  
  
 雖然`GetModuleInfo2`可能會呼叫方法，只要有模組 ID，無法使用父組件的識別碼，直到程式碼剖析工具收到[icorprofilercallback:: Moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)回呼。  
  
 當 `GetModuleInfo2` 傳回時，您必須確認 `szName` 緩衝區的大小足以包含模組的完整檔案名稱。 若要這樣做，請比對 `pcchName` 指向的值和 `cchName` 參數。 如果 `pcchName` 指向大於 `cchName` 的值，請配置較大的 `szName` 緩衝區，並以較大的大小來更新 `cchName`，然後再次呼叫 `GetModuleInfo2`。  
  
 或者，您也可以先使用長度為零的 `szName` 緩衝區來呼叫 `GetModuleInfo2`，以取得正確的緩衝區大小。 接著您就可以將緩衝區大小設定為 `pcchName` 中傳回的值，並再次呼叫 `GetModuleInfo2`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
