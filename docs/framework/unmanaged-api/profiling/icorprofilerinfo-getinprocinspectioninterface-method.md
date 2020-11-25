---
title: ICorProfilerInfo::GetInprocInspectionInterface 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
ms.openlocfilehash: cc8bdfb1e46e5304227a40f869856f07e1f90bed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707486"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a>ICorProfilerInfo::GetInprocInspectionInterface 方法

取得可針對 "ICorDebugProcess" 介面進行查詢的物件。 此方法在 .NET Framework 版本2.0 中已淘汰。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>參數  

 `ppicd`  
 可針對介面進行查詢的[out](/cpp/atl/iunknown)物件 `ICorDebugProcess` 。  
  
## <a name="remarks"></a>備註  

 Common language runtime (CLR) 偵錯工具開發介面支援在 .NET Framework 1.0 版中進行有限的進程內進行中的偵錯工具。 同進程的偵錯工具可讓分析工具使用偵錯工具 API 的檢查部分。 由於客戶的意見反應，已從2.0 版中的 .NET Framework 移除同進程的偵錯工具，並以一組與分析 API 更同行的功能取代。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1。0  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
