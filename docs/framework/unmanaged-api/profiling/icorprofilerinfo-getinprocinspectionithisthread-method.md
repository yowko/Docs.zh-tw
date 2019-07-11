---
title: ICorProfilerInfo::GetInprocInspectionIThisThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e0f56dd6ece32b1f05418ea288da409af5cad5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782757"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread 方法
ICorDebugThread 介面取得的可查詢的物件。 這個方法是在.NET Framework 2.0 版中已過時。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>參數  
 `ppicd`  
 [out](/cpp/atl/iunknown)物件，可以查詢`ICorDebugThread`介面。  
  
## <a name="remarks"></a>備註  
 Common language runtime (CLR) 偵錯服務支援有限的處理序中的偵錯.NET Framework 1.0 版。 若要使用偵錯 API 檢查部分的程式碼剖析工具啟用同處理序偵錯。 因為客戶的意見反應，而同處理序偵錯已移除從.NET Framework 2.0 版中，並取代為一組更符合程式碼剖析 API 的功能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** 1.0  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
