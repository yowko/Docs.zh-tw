---
title: 'CloneEnumWbemClassObject 函式 (非受控 API 參考) '
description: CloneEnumWbemClassObject 函式會建立列舉值的邏輯複本。
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fa8a7f436c018e3e083be452d300eb21e17f93f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708123"
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject 函式

建立列舉程式的邏輯複本，並保留其在列舉中的目前位置。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a>參數

`ppEnum`\
擴展接收新 [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)的指標。

`authLevel`\
在授權層級。

`impLevel`\
在模擬等級。

`pCurrentEnumWbemClassObject`\
擴展要複製之 [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) 實例的指標。

`strUser`\
在使用者名稱。 如需詳細資訊，請參閱 [ConnectServerWmi](connectserverwmi.md) 函數。

`strPassword`\
在密碼。 如需詳細資訊，請參閱 [ConnectServerWmi](connectserverwmi.md) 函數。

`strAuthority`\
在使用者的功能變數名稱。 如需詳細資訊，請參閱 [ConnectServerWmi](connectserverwmi.md) 函數。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成此作業。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的進程與 WMI 之間 (RPC) 連結的遠端程序呼叫失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函數會包裝對 [IEnumWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) 方法的呼叫。

這種方法只會產生「最大努力」的複製。 由於許多 CIM 物件的動態本質，新的列舉值可能不會列舉與來源列舉值相同的物件集合。

如果函式呼叫失敗，您可以藉由呼叫 [GetErrorInfo](geterrorinfo.md) 函數來取得額外的錯誤資訊。

## <a name="example"></a>範例

如需範例，請參閱 [IEnumWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) 方法。

## <a name="requirements"></a>需求

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。

 **標頭：** WMINet_Utils .idl

 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
