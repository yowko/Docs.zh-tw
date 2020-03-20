---
title: 設置安全功能（非託管 API 引用）
description: SetSecurity 函數檢索當前執行緒的類比權杖。
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
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176730"
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
[出]當函數返回時，包含指向 的`boolean`指標，指示是否應通過調用[ResetSecurity](resetsecurity.md)函數重置權杖。

`token`\
[出]當函數返回時，包含指向與當前執行緒關聯的類比權杖控制碼的指標。 如果沒有與當前執行緒`null`關聯的權杖，則其值可以是。

## <a name="return-value"></a>傳回值

如果函數成功，則傳回值為`S_OK`（0）。

如果函數失敗，傳回值是非零錯誤代碼。 要獲取擴展的錯誤資訊，請致電[GetErrorInfo](geterrorinfo.md)函數。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標題：** WMINet_Utils.idl

 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
