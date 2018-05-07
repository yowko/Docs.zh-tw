---
title: FormatFromRawValue 函式 （Unmanaged API 參考）
description: FormatFromRawValue 函式會將未經處理的效能資料轉換成指定的格式。
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
ms.openlocfilehash: e0710b26237b350f1dfbc7d2464b7a131373604e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue 函式
將指定的格式，一個的未經處理的效能資料值或兩個原始效能資料值的轉換，如果格式轉換是以時間為基礎。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
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

`dwCounterType`  
[in]計數器類型。 如需計數器類型的清單，請參閱[WMI 效能計數器型別](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx)。 `dwCounterType` 可以是除了任何計數器類型`PERF_LARGE_RAW_FRACTION`和`PERF_LARGE_RAW_BASE`。 

`dwFormat`  
[in]要轉換的未經處理的效能資料的格式。 它可以是下列值之一：

|常數  |值  |描述 |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | 傳回的導出的值做為雙精確度浮點數值。 | 
| `PDH_FMT_LARGE` | 0x00000400 | 以 64 位元整數的形式傳回導出的值。 |
| `PDH_FMT_LONG` | 0x00000100 | 以 32 位元整數的形式傳回導出的值。 |

其中一個先前的值可以是其中一個下列調整旗標 ORed:

|常數  |值  |描述 |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | 不會套用計數器的縮放比例。 |
| `PDH_FMT_1000` | 0x00002000 | 最終的值乘以 1000。 | 

`pTimeBase`  
[in]如果所需的格式轉換的時間基底指標。 如果找不到所需的格式轉換的時間基底的資訊，則會忽略此參數的值。

`pRawValue1` [in]指標[ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)結構，表示原始效能值。

`pRawValue2` [in]指標[ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)結構，表示第二個的未經處理的效能值。 如果第二個的未經處理的效能值不是必要的這個參數應該是`null`。

`pFmtValue` [out]指標[ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx)接收格式化的效能值的結構。

## <a name="return-value"></a>傳回值

這個函式會傳回下列值：

|常數  |值  |描述  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | 函式呼叫會成功。 |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | 必要的引數已遺失或不正確。 | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | 控制代碼不是有效的 PDH 物件。 |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx)函式。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **程式庫：** PerfCounter.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
