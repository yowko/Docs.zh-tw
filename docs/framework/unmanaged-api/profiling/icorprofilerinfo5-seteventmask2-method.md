---
title: ICorProfilerInfo5::SetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 8027cdcde8281c363207e309bf65fcd90c03b626
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495615"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 設定值，以指定分析工具要從通用語言執行時期 (CLR) 接收事件通知之來源事件的類型。 它提供的功能比[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法更多。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwEventsLow`  
 [in] 4 個位元組的值，可指定事件的分類。 每個位元各控制事件的不同功能、行為或類型。 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉中會描述位。  
  
 `dwEventsHigh`  
 [in] 4 個位元組的值，可指定事件的分類。  每個位元各控制事件的不同功能、行為或類型。 [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md)列舉中會描述位。  
  
## <a name="remarks"></a>備註  
 `SetEventMask2` 方法可用於設定分析工具所訂閱的回呼。 一般來說，您會呼叫[GetEventMask2](icorprofilerinfo5-geteventmask2-method.md)方法來判斷已設定的位、執行其和值的邏輯 OR， `pdwEventsLow` `pdwEventsHigh` 以及您想要設定的任何新位，然後再呼叫 `SetEventMask2` 方法。  
  
 這是[SetEventMask](icorprofilerinfo-seteventmask-method.md)方法的建議替代方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo5 介面](icorprofilerinfo5-interface.md)
- [GetEventMask2 方法](icorprofilerinfo5-geteventmask2-method.md)
