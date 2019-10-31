---
title: SetSecurity 函式（非受控 API 參考）
description: SetSecurity 函數會抓取目前線程的模擬 token。
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6d27779bcfc97e1c4156b8782896e83d4754491b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120218"
---
# <a name="setsecurity-function"></a>SetSecurity 函式

擷取與目前執行緒關聯的模擬權杖。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a>參數

`pNeedToReset`\
脫銷當函式傳回時，會包含 `boolean` 的指標，指出是否應該藉由呼叫[ResetSecurity](resetsecurity.md)函數來重設權杖。

`token`\
脫銷當函式傳回時，會包含與目前線程相關聯之模擬標記的控制碼指標。 如果沒有與目前線程相關聯的 token，則其值可以 `null`。 

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值會是 `S_OK` （0）。

如果函式失敗，則傳回值為非零的錯誤碼。 若要取得擴充的錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** WMINet_Utils .idl

 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
