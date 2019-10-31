---
title: ICorProfilerInfo5::GetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: 2e814eaba04fd6781d10bbcb67ade9acdefa161d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114740"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>ICorProfilerInfo5::GetEventMask2 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 取得分析工具想要從 Common Language Runtime (CLR) 接收通知的目前事件分類。  它提供了[ICorProfilerInfo：： GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)方法未提供的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwEventsLow`  
 [out] 指定事件分類的 4 位元組值的指標。 每個位元各控制事件的不同功能、行為或類型。 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉中會說明此位。  
  
 `pdwEventsHigh`  
 [out] 指定事件分類的 4 位元組值的指標。  每個位元各控制事件的不同功能、行為或類型。 [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)列舉中會說明此位。  
  
## <a name="remarks"></a>備註  
 `GetEventMask2` 方法可用於判斷分析工具已訂閱哪些回呼。 一般來說，您會執行 `pdwEventsLow` 的邏輯 OR，並 `pdwEventsHigh` 值和任何您想要設定的新位，然後再呼叫[SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。  
  
 這是[GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)方法的建議替代方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo5 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [SetEventMask2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
