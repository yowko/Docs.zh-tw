---
title: ConnectServerWmi 函式 （Unmanaged API 參考）
description: ConnectServerWmi 函式會使用 DCOM 來建立連線至 WMI 命名空間。
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
ms.openlocfilehash: 163e61eef8a753b5b6470285e5e3ce63789e25a4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45675752"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi 函式
在指定的電腦上建立從 DCOM 到 WMI 命名空間的連線。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
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

`strNetworkResource` [in]為有效的指標`BSTR`包含正確的 WMI 命名空間的物件路徑。 請參閱[備註](#remarks)節的詳細資訊。

`strUser` [in]有效的指標`BSTR`，其中包含使用者名稱。 A`null`值表示目前的安全性內容。 如果使用者是從不同的網域，目前於`strUser`也可以包含反斜線分隔的網域和使用者名稱。 `strUser` 也可以是在 使用者主體名稱 (UPN) 格式化，為 suhc *userName@domainName*。 請參閱[備註](#remarks)節的詳細資訊。

`strPassword` [in]有效的指標`BSTR`其中包含的密碼。 A`null`指出目前的安全性內容。 空字串 ("") 表示有效的長度為零的密碼。

`strLocale` [in]有效的指標`BSTR`指出正確的地區設定的資訊擷取。 Microsoft 地區設定識別項、 字串的格式是 「 MS\_*xxx*"，其中*xxx*是十六進位格式表示的地區設定識別碼 (LCID) 的字串。 如果未指定無效的地區設定，則方法會傳回`WBEM_E_INVALID_PARAMETER`在 Windows 7，改為使用伺服器的預設地區設定是除外。 如果 ' null1，目前的地區設定使用。 
 
`lSecurityFlags` [in]旗標傳遞至`ConnectServerWmi`方法。 零 (0) 這個參數的值會導致呼叫`ConnectServerWmi`建立連接到伺服器之後，才傳回。 這可能導致應用程式沒有回應無限期地如果伺服器將會中斷。 其他有效值為：

| 常數  | 值  | 描述  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | 保留供內部使用。 請勿使用。 |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` 傳回在兩分鐘或更短。 |

`strAuthority` [in]使用者的網域名稱。 它可以包含下列值：

| 值 | 描述 |
|---------|---------|
| 空白 | 使用 NTLM 驗證，並會使用目前使用者的 NTLM 網域。 如果`strUser`指定網域 （建議的位置），它必須不在這裡指定。 此函數會傳回`WBEM_E_INVALID_PARAMETER`如果您在這兩個參數中指定的網域。 |
| Kerberos:*主體名稱* | 使用 Kerberos 驗證，且此參數包含 Kerberos 主體名稱。 |
| NTLMDOMAIN:*網域名稱* | 使用 NT LAN Manager 驗證，且此參數包含的 NTLM 網域名稱。 |

`pCtx`   
[in]一般而言，這個參數是`null`。 否則，它是指標[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)所需的一或多個動態類別提供者的物件。 

`ppNamespace`  
[out]當函式傳回時，收到的指標[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件繫結至指定的命名空間。 它會設定為指向`null`時卻發生錯誤。

`impLevel`  
[in]模擬等級。

`authLevel`  
[in]授權層級。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx)方法。

 在預設命名空間中，本機存取`strNetworkResource`可以是簡單的物件路徑:"root\default"或"\\.\root\default"。 存取遠端電腦上的預設命名空間使用 COM 或 Microsoft 相容的網路功能，包含電腦名稱:"\\myserver\root\default"。 電腦名稱也可以是 DNS 名稱或 IP 位址。 `ConnectServerWmi`函式也可以執行 IPv6 的電腦連線使用 IPv6 位址。

`strUser` 不可以是空的字串。 如果在指定網域`strAuthority`，它不也必須包含在`strUser`，或函式會傳回`WBEM_E_INVALID_PARAMETER`。


## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
