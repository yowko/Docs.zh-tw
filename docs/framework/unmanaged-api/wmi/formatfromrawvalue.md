---
title: FormatFromRawValue 函式 (非受控 API 參考)
description: FormatFromRawValue 函數會將原始效能資料轉換成指定的格式。
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 681d7ce42b2b8d16353e4f5b3523f1a953a49d95
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037891"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue 函式
將一個原始效能資料值轉換為指定的格式，或轉換為兩個原始效能資料值 (若格式轉換是以時間為基礎)。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a>參數

`dwCounterType`\
在計數器類型。 如需計數器類型的清單, 請參閱[WMI 效能計數器類型](/windows/desktop/WmiSdk/wmi-performance-counter-types)。 `dwCounterType`可以是任何計數器類型`PERF_LARGE_RAW_FRACTION` , 但和`PERF_LARGE_RAW_BASE`除外。 

`dwFormat`\
在要轉換原始效能資料的格式。 它可以是下列其中一個值:

|常數  |值  |說明 |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | 傳回計算的值做為雙精確度浮點值。 | 
| `PDH_FMT_LARGE` | 0x00000400 | 以64位整數傳回計算的值。 |
| `PDH_FMT_LONG` | 0x00000100 | 以32位整數傳回計算的值。 |

先前的其中一個值可以使用下列其中一個調整旗標來 ORed:

|常數  |值  |描述 |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | 請勿套用計數器的縮放比例。 |
| `PDH_FMT_1000` | 0x00002000 | 將最後一個值乘以1000。 | 

`pTimeBase`\
在如果需要格式轉換, 則為時間基底的指標。 如果格式轉換不需要時間基底資訊, 則會忽略這個參數的值。

`pRawValue1`\ [in] [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter)結構的指標, 表示原始的效能值。

`pRawValue2`\
在[`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter)結構的指標, 表示第二個原始的效能值。 如果不需要第二個原始效能值, 這個參數應該是`null`。

`pFmtValue`\
脫銷接收格式化效能值[`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue)之結構的指標。

## <a name="return-value"></a>傳回值

此函式會傳回下列值:

|常數  |值  |描述  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | 函數呼叫成功。 |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | 缺少必要的引數或其不正確。 | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | 控制碼不是有效的 PDH 物件。 |

## <a name="remarks"></a>備註

此函式會包裝對[FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))函數的呼叫。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

 **LIBRARY:** PerfCounter.dll

 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 (非受控 API 參考)](index.md)
