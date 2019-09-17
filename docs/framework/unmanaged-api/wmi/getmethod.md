---
title: GetMethod 函式（非受控 API 參考）
description: GetMethod 函數會抓取方法的相關資訊。
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798574"
---
# <a name="getmethod-function"></a>GetMethod 函式

擷取指定之方法的相關資訊。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a>參數

`vFunc`\
在未使用此參數。

`ptr`\
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`wszName`\
在方法名稱。 這個參數不可以`null`是，而且必須指向有效`LPCWSTR`的。

`lFlags`\
[in] 保留。 這個參數必須是0。

`ppInSignature`\
脫銷[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例位址的指標，描述方法的 in 參數。 如果設定為， `null`則會忽略這個參數。

`ppOutSignature`\
脫銷[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例之位址的指標，描述方法的 out 參數。 如果設定為， `null`則會忽略這個參數。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 找不到指定的屬性。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)方法的呼叫。

如果方法中沒有 in 參數，Windows `null`管理可以將 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 指標設定為。

在`ppInSignature` `IWbemClassObject`和`ppOutSignature`中，分別描述 in 和 out 參數，當做 system 類別[_Parameters](/windows/desktop/WmiSdk/--parameters)之實例中的屬性。 `ppInSignature`中的屬性會命名`Param`為*n*，其中*n*是方法簽章中參數的位置（例如`Param1`、 `Param2`等）。 中`ppOutSignature`的屬性也會命名`Param`為*n*，而傳回值會命名`ReturnValue`為。 如需詳細資訊和範例，請參閱[IWbemClassObject：： GetMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
