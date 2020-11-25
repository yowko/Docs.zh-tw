---
title: 'CreateClassEnumWmi 函式 (非受控 API 參考) '
description: CreateClassEnumWmi 函數會傳回符合指定準則之所有類別的枚舉器。
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b80954e288f6720c75d0af0b8af083fa4856754
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719732"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi 函式

傳回滿足所指定選取條件之所有類別的列舉程式。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>參數

`strSuperclass`\
在如果不是 `null` 或空白，則指定父類別的名稱; 列舉值只會傳回這個類別的子類別。 如果是 `null` 或空白且 `lFlags` 為 WBEM_FLAG_SHALLOW，則只會傳回最上層類別 (沒有父類別) 的類別。 如果是 `null` 或空白，而且 `lFlags` 是，則會傳回 `WBEM_FLAG_DEEP` 命名空間中的所有類別。

`lFlags`\
在影響此函數行為的旗標組合。 下列值定義于 *WbemCli .h* 標頭檔中，您也可以在程式碼中將其定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果設定，則函式會抓取儲存在目前連接地區設定之當地語系化命名空間中的已修改限定詞。 <br/> 如果未設定，則函式只會抓取立即命名空間中儲存的限定詞。 |
| `WBEM_FLAG_DEEP` | 0 | 列舉包含階層中的所有子類別，但不包含這個類別。 |
| `WBEM_FLAG_SHALLOW` | 1 | 列舉只包含這個類別的純實例，並排除提供在這個類別中找不到之屬性的所有子類別實例。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 函數會傳回順向列舉值。 一般來說，順向列舉值會比傳統列舉值更快且使用較少的記憶體，但不允許呼叫 [複製](clone.md)。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI 會保留列舉中物件的指標，直到釋放它們為止。 |

建議的旗標為 `WBEM_FLAG_RETURN_IMMEDIATELY` ， `WBEM_FLAG_FORWARD_ONLY` 以獲得最佳效能。

`pCtx`\
在通常，這個值是 `null` 。 否則，它是 [IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) 實例的指標，可供提供要求之類別的提供者使用。

`ppEnum`\
擴展接收列舉值的指標。

`authLevel`\
在授權層級。

`impLevel`\
在模擬等級。

`pCurrentNamespace`\
在代表目前命名空間之 [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) 物件的指標。

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
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有許可權可查看函式可以傳回的一或多個類別。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` 不存在。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 可能已停止並重新啟動。 再次呼叫 [ConnectServerWmi](connectserverwmi.md) 。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的進程與 WMI 之間 (RPC) 連結的遠端程序呼叫失敗。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函數會包裝對 [IWbemServices：： CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) 方法的呼叫。

如果函式呼叫失敗，您可以藉由呼叫 [GetErrorInfo](geterrorinfo.md) 函數來取得額外的錯誤資訊。

## <a name="requirements"></a>需求

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils .idl

**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
