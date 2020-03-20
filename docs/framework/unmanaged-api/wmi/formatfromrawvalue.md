---
title: 格式從原始值函數（非託管 API 引用）
description: FormatFromRawValue 函數將原始效能資料轉換為指定的格式。
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
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176834"
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
[在]計數器類型。 有關計數器類型的清單，請參閱[WMI 效能計數器類型](/windows/desktop/WmiSdk/wmi-performance-counter-types)。 `dwCounterType`可以是 除`PERF_LARGE_RAW_FRACTION`和`PERF_LARGE_RAW_BASE`之外的任何計數器類型。

`dwFormat`\
[在]要將原始效能資料轉換為的格式。 它可能是下列其中一個值：

|持續性  |值  |描述 |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | 將計算值作為雙精度浮點值返回。 |
| `PDH_FMT_LARGE` | 0x00000400 | 將計算的值作為 64 位整數返回。 |
| `PDH_FMT_LONG` | 0x00000100 | 將計算的值作為 32 位整數返回。 |

前面的值之一可以是 ORed，具有以下縮放標誌之一：

|持續性  |值  |描述 |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | 不要應用計數器的縮放因數。 |
| `PDH_FMT_1000` | 0x00002000 | 將最終值乘以 1，000。 |

`pTimeBase`\
[在]指向時間基的指標，如果需要進行格式轉換。 如果格式轉換不需要時間基礎資訊，則忽略此參數的值。

`pRawValue1`\
[在]指向表示原始性能[`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter)值的結構的指標。

`pRawValue2`\
[在]指向表示第二[`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter)個原始性能值的結構的指標。 如果不需要第二個原始性能值，則此參數應為`null`。

`pFmtValue`\
[出]指向接收格式化性能[`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue)值的結構的指標。

## <a name="return-value"></a>傳回值

此函數返回以下值：

|持續性  |值  |描述  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | 函式呼叫成功。 |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | 所需的參數丟失或不正確。 |
| `PDH_INVALID_HANDLE` | 0xC00000BBC | 控制碼不是有效的 PDH 物件。 |

## <a name="remarks"></a>備註

此函數將調用格式[從RawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))函數結束。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **庫：** 佩爾夫·德雷爾

 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
