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
ms.openlocfilehash: 0ab383f0968061667b3580a2058687eecda99dde
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869994"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread 方法
取得可針對 ICorDebugThread 介面查詢的物件。 這個方法在 .NET Framework 版本2.0 中已過時。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>參數  
 `ppicd`  
 [out](/cpp/atl/iunknown)物件，可查詢 `ICorDebugThread` 介面。  
  
## <a name="remarks"></a>備註  
 Common language runtime （CLR）偵錯工具在 .NET Framework 版本1.0 中支援有限的同進程偵錯工具。 同進程的偵錯工具已啟用分析工具，以使用偵錯工具開發介面的檢查部分。 由於客戶意見反應的結果，已從版本2.0 中的 .NET Framework 中移除同進程的偵錯工具，並以一組與分析 API 更符合的功能來取代。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.0  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
