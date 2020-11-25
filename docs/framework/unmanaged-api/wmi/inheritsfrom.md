---
title: 'InheritsFrom 函式 (非受控 API 參考) '
description: InheritsFrom 函式會判斷類別或實例是否衍生自特定的父類別。
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3cfe3388dc808335e6d3daaf7ec949108e95f52e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726784"
---
# <a name="inheritsfrom-function"></a>InheritsFrom 函式

判斷目前類別或執行個體衍生自指定的父類別。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a>參數

`vFunc`  
在此參數未使用。

`ptr`  
在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。

`wszAncestor`  
在類別的名稱。 `wszAncestor` 必須指向有效的 `LPCWSTR` 。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | 目前的物件繼承自 `wszAncestor` 。  |
| `WBEM_S_FALSE` | 1 | 目前的物件不是繼承自 `wszAncestor` 。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` 為 `null`。 |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：： InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) 方法的呼叫。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
