---
title: ICorProfilerInfo::GetModuleMetaData 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 62b34128be99ce7750d45e6c19e26bef7fcc98c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502947"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData 方法
取得對應至指定模組的中繼資料介面實例。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 在介面實例將對應之模組的識別碼。  
  
 `dwOpenFlags`  
 在[CorOpenFlags](../metadata/coropenflags-enumeration.md)列舉的值，指定用來開啟資訊清單檔案的模式。 只有 `ofRead` 、 `ofWrite` 和 `ofNoTransform` 位有效。  
  
 `riid`  
 在將抓取其實例之中繼資料介面的參考識別碼（GUID）。 如需介面的清單，請參閱[中繼資料介面](../metadata/metadata-interfaces.md)。  
  
 `ppOut`  
 脫銷中繼資料介面實例位址的指標。  
  
## <a name="remarks"></a>備註  
 您可以要求在讀取/寫入模式中開啟中繼資料，但這會導致程式的中繼資料執行速度較慢，因為對中繼資料所做的變更無法根據來自編譯器的方式優化。  
  
 有些模組（例如資源模組）沒有中繼資料。 在這些情況下， `GetModuleMetaData` 將會傳回 S_FALSE 的 HRESULT 值，而 * 中會傳回 null `ppOut` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
