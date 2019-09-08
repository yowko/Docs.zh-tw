---
title: CreateClassEnumWmi 函式（非受控 API 參考）
description: CreateClassEnumWmi 函數會傳回符合指定準則之所有類別的列舉值。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a696a6f02f6d3a5afbcb45e5566e4b667739e2c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798737"
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
在如果不`null`是或空白，會指定父類別的名稱; 枚舉器只會傳回這個類別的子類別。 如果是`null`或空白，而且`lFlags`是 WBEM_FLAG_SHALLOW，則只會傳回最上層類別（沒有父類別的類別）。 如果是`null`或空白，而且`lFlags`為`WBEM_FLAG_DEEP`，則會傳回命名空間中的所有類別。

`lFlags`\
在會影響此函式行為的旗標組合。 下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果設定，函式會抓取已修改的限定詞，並儲存在目前連接地區設定的當地語系化命名空間中。 <br/> 如果未設定，此函式只會抓取立即命名空間中儲存的限定詞。 |
| `WBEM_FLAG_DEEP` | 0 | 列舉包括階層中的所有子類別，但不包含這個類別。 |
| `WBEM_FLAG_SHALLOW` | 1 | 列舉只包含這個類別的純實例，而且會排除提供此類別中找不到之屬性的所有子類別實例。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 函數會傳回順向列舉值。 一般來說，順向列舉值的速度較快，而且使用的記憶體比傳統的列舉值少，但它們不允許[複製](clone.md)的呼叫。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI 會保留列舉中物件的指標，直到釋放它們為止。 |

建議的旗標`WBEM_FLAG_RETURN_IMMEDIATELY`為`WBEM_FLAG_FORWARD_ONLY` ，以達到最佳效能。

`pCtx`\
在通常，此值為`null`。 否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求之類別的提供者使用。

`ppEnum`\
脫銷接收列舉值的指標。

`authLevel`\
在授權層級。

`impLevel`\
在模擬層級。

`pCurrentNamespace`\
在[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件的指標，表示目前的命名空間。

`strUser`\
在使用者名稱。 如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

`strPassword`\
在密碼。 如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

`strAuthority`\
在使用者的功能變數名稱。 如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有許可權可查看函數可以傳回的一個或多個類別。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` 不存在。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 可能已停止並重新啟動。 再次呼叫[ConnectServerWmi](connectserverwmi.md) 。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemServices：： CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum)方法的呼叫。

如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
