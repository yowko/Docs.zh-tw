---
title: ConnectServerWmi 函式（非受控 API 參考）
description: ConnectServerWmi 函數會使用 DCOM 來建立與 WMI 命名空間的連線。
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ebb268dcee877f4e9aea0c88852333897030dd1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798748"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi 函式

在指定的電腦上建立從 DCOM 到 WMI 命名空間的連線。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a>參數

`strNetworkResource`\
在有效`BSTR`的指標，其中包含正確 WMI 命名空間的物件路徑。 如需詳細資訊，請參閱[備註](#remarks)一節。

`strUser`\
在包含使用者名稱之有效`BSTR`的指標。 `null`值表示目前的安全性內容。 如果使用者與目前的網域不同， `strUser`則也可以包含以反斜線分隔的網域和使用者名稱。 `strUser`也可以是使用者主體名稱（UPN）格式，例如`userName@domainName`。 如需詳細資訊，請參閱[備註](#remarks)一節。

`strPassword`\
在包含密碼的有效`BSTR`指標。 `null`表示目前的安全性內容。 空字串（""）表示有效的長度為零的密碼。

`strLocale`\
在有效`BSTR`的指標，表示資訊抓取的正確地區設定。 針對 Microsoft 地區設定識別碼，字串的格式為 "MS\_ *xxx*"，其中*xxx*是十六進位格式的字串，表示地區設定識別碼（LCID）。 如果指定了不正確地區設定，此方法`WBEM_E_INVALID_PARAMETER`會傳回，但在 Windows 7 上，會改為使用伺服器的預設地區設定。 如果為 ' null1，則會使用目前的地區設定。

`lSecurityFlags`\
在要傳遞至方法的`ConnectServerWmi`旗標。 這個參數的值為零（0），會導致只有在建立`ConnectServerWmi`與伺服器的連接之後，才會傳回傳回的呼叫。 這可能會導致應用程式在伺服器中斷時不會無限期回應。 其他有效的值為：

| 常數  | 值  | 描述  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | 保留供內部使用。 請勿使用。 |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`傳回兩分鐘以內。 |

`strAuthority`\
在使用者的功能變數名稱。 它可以包含下列值：

| 值 | 描述 |
|---------|---------|
| 空白 | 使用 NTLM 驗證，並使用目前使用者的 NTLM 網域。 如果`strUser`指定網域（建議的位置），則不得在此指定。 `WBEM_E_INVALID_PARAMETER`如果您在這兩個參數中指定網域，則此函式會傳回。 |
| Kerberos：*主體名稱* | 使用 kerberos 驗證，且此參數包含 Kerberos 主體名稱。 |
| NTLMDOMAIN：*功能變數名稱* | 使用 NT LAN Manager 驗證，且此參數包含 NTLM 功能變數名稱。 |

`pCtx`\
在一般而言，此參數為`null`。 否則，它是一或多個動態類別提供者所需之[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)物件的指標。

`ppNamespace`\
脫銷當函式傳回時，會接收系結至指定之命名空間之[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件的指標。 `null`當發生錯誤時，它會設定為指向。

`impLevel`\
在模擬層級。

`authLevel`\
在授權層級。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemLocator：： ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver)方法的呼叫。

對於預設命名空間的本機存取， `strNetworkResource`可以是簡單的物件路徑： "root\default" 或 "\\.\root\default"。 若要使用 COM 或與 Microsoft 相容的網路存取遠端電腦上的預設命名空間，請包含電腦名稱稱：\\"myserver\root\default"。 電腦名稱稱也可以是 DNS 名稱或 IP 位址。 此`ConnectServerWmi`函式也可以使用 ipv6 位址來連線到執行 ipv6 的電腦。

`strUser`不可以是空字串。 如果在中`strAuthority`指定了網域，它也不能包含在`strUser`中`WBEM_E_INVALID_PARAMETER`，否則函數會傳回。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** WMINet_Utils.idl

 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
