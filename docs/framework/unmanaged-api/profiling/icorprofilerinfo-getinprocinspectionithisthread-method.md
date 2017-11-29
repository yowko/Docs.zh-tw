---
title: "ICorProfilerInfo::GetInprocInspectionIThisThread 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionIThisThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9a260143e36939f4201d7949f5783f80e5c20ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread 方法
ICorDebugThread 介面取得的可查詢的物件。 這個方法是.NET Framework 2.0 版中已過時。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a>參數  
 `ppicd`  
 [out](/cpp/atl/iunknown)可以查詢的物件`ICorDebugThread`介面。  
  
## <a name="remarks"></a>備註  
 Common language runtime (CLR) 偵錯服務支援有限的處理序中的偵錯.NET Framework 1.0 版。 若要使用偵錯 API 檢查部份程式碼剖析工具啟用同處理序偵錯。 客戶的意見反應，因為同處理序偵錯具有已經從.NET Framework 2.0 版中移除和取代的功能與程式碼剖析 API 對齊多個一組。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.0  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
