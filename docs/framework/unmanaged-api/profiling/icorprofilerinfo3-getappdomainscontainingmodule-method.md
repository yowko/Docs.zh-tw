---
title: ICorProfilerInfo3::GetAppDomainsContainingModule 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
ms.openlocfilehash: 8615deb2e42b039120d97b3eb5af23beb31b0808
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502843"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a>ICorProfilerInfo3::GetAppDomainsContainingModule 方法
取得已載入指定模組之應用程式定義域的識別項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a>參數  
 `moduleId`  
 [in] 載入模組的 ID。  
  
 `cAppDomainIds`  
 [in] `appDomainIds` 陣列的大小。  
  
 `pcAppDomainIds`  
 [out] 傳回項目之總數的指標。  
  
 `appDomainIds`  
 [out] 應用程式定義域 ID 值的陣列。  
  
## <a name="remarks"></a>備註  
 這個方法會使用呼叫端配置的緩衝區。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerFunctionEnum 介面](icorprofilerfunctionenum-interface.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
