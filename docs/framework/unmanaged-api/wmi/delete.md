---
title: Delete 函式（非受控 API 參考）
description: Delete 函式會從 CIM 類別定義中刪除指定的屬性及其所有限定詞。
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1bf9bd5d93d1affee649588138456269411d280
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798677"
---
# <a name="delete-function"></a>Delete 函式

從 CIM 類別定義中刪除指定的屬性及其所有限定詞。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a>參數

`vFunc`\
在未使用此參數。

`ptr`\
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`wszName`\
在要刪除的屬性名稱。 `wszName`必須是有效`LPCWSTR`的指標。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | 無法刪除屬性。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` 無效。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | 指定的屬性不存在。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 記憶體不足，無法完成操作。 |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | 屬性繼承自基類。 |
| `WBEM_E_SYSTEM_PROPERTY` | | 屬性是系統屬性。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | 函式已刪除目前類別的覆寫預設值。 父類別中這個屬性的預設值已重新開機。 |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：:D 刪除](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete)方法的呼叫。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
