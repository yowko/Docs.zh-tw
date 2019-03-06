---
title: GetMethod 函式 （Unmanaged API 參考）
description: GetMethod 函式會擷取方法的相關資訊。
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
ms.openlocfilehash: cb8919e8760616676ea5ff99069e2d2ceb5f7451
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370692"
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
[in]未使用此參數。

`ptr`\
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`wszName`\
[in]方法名稱。 這個參數不能`null`而且必須指向有效`LPCWSTR`。

`lFlags`\
[in] 保留。 這個參數必須是 0。

`ppInSignature`\
[out]位址指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)描述中的參數至方法的執行個體。 如果設定為，則會忽略這個參數`null`。

`ppOutSignature`\
[out]位址指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)描述方法的 out 參數的執行個體。 如果設定為，則會忽略這個參數`null`。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 找不到指定的屬性。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)方法。

Windows 管理可以設定[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標`null`如果方法沒有任何 in 參數。

在 `ppInSignature`並`ppOutSignature`分別中的屬性描述輸入和輸出參數，`IWbemClassObject`系統類別的執行個體[_Parameters](/windows/desktop/WmiSdk/--parameters)。 中的屬性`ppInSignature`具名`Param` *n*，其中*n*是方法簽章中參數的位置 (例如`Param1`， `Param2`，依此類推。)。 中的屬性`ppOutSignature`也稱為`Param` *n*，和名為傳回值`ReturnValue`。 如需詳細資訊和範例，請參閱 < [IWbemClassObject::GetMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)