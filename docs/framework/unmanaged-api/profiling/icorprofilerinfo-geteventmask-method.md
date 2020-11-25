---
title: ICorProfilerInfo::GetEventMask 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
ms.openlocfilehash: 16bd8b09d5118171e669e9c428fb444384b5867d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722560"
---
# <a name="icorprofilerinfogeteventmask-method"></a>ICorProfilerInfo::GetEventMask 方法

取得分析工具想要從 Common Language Runtime (CLR) 接收事件通知的目前事件分類。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a>參數  

 `pdwEvents`  
 [out] 指定事件分類的 4 位元組值的指標。 每個位元各控制事件的不同功能、行為或類型。 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉中會說明這些位。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 您應呼叫 [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) 方法，而不是此方法。 雖然此 `SetEventMask` 方法會繼續受到支援，但 [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) 會提供額外的功能。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetEventMask2 方法](icorprofilerinfo5-geteventmask2-method.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
