---
title: "ConnectServerWmi 函式 （Unmanaged API 參考）"
description: "ConnectServerWmi 函式會使用 DCOM 進行建立的 WMI 命名空間的連接。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ConnectServerWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ConnectServerWmi
helpviewer_keywords: ConnectServerWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc821bddf1d33ea1144fef0821b81cf027d8f92f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi 函式
指定在電腦上建立的 WMI 命名空間透過與 DCOM 的連線。  
  
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

`strNetworkResource`[in]有效的指標`BSTR`包含正確的 WMI 命名空間的物件路徑。 請參閱[備註](#remarks)節的詳細資訊。

`strUser`[in]有效的指標`BSTR`，其中包含使用者名稱。 A`null`值會指出目前的安全性內容。 如果使用者是目前的不同的網域從`strUser`也可以包含反斜線分隔的網域和使用者名稱。 `strUser`也可以是在使用者主要名稱 (UPN) 格式化，做為 suhc  *userName@domainName* 。 請參閱[備註](#remarks)節的詳細資訊。

`strPassword`[in]有效的指標`BSTR`其中包含的密碼。 A`null`指出目前的安全性內容。 空字串 ("") 表示有效長度為零的密碼。

`strLocale`[in]有效的指標`BSTR`，指出資訊擷取正確的地區設定。 Microsoft 地區設定識別項，字串的格式為"MS\_*xxx*"，其中*xxx*是以十六進位格式表示的地區設定識別碼 (LCID) 的字串。 如果未指定無效的地區設定，則方法會傳回`WBEM_E_INVALID_PARAMETER`除了 Windows 7，改為使用伺服器的預設地區設定是。 如果 ' null1，目前的地區設定使用。 
 
`lSecurityFlags`[in]旗標，以傳遞至`ConnectServerWmi`方法。 值為零 (0) 為此參數會導致在呼叫`ConnectServerWmi`建立連接到伺服器之後，才傳回。 這可能導致應用程式沒有回應無限期的伺服器已中斷。 其他有效值為：

| 常數  | 值  | 描述  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | 保留供內部使用。 請勿使用。 |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`傳回在兩分鐘或更短。 |

`strAuthority`[in]使用者的網域名稱。 它可以包含下列值：

| 值 | 描述 |
|---------|---------|
| 空白 | 使用 NTLM 驗證，並會使用目前使用者的 NTLM 網域。 如果`strUser`指定網域 （建議的位置），它必須不在這裡指定。 此函數會傳回`WBEM_E_INVALID_PARAMETER`如果您在這兩個參數中指定的網域。 |
| Kerberos:*主體名稱* | 使用 Kerberos 驗證，以及這個參數會包含一個 Kerberos 主要名稱。 |
| NTLMDOMAIN:*網域名稱* | 如果使用 NT LAN Manager 驗證，這個參數會包含 NTLM 網域名稱。 |

`pCtx`   
[in]一般而言，這個參數是`null`。 否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx)所需的一個或多個動態類別提供者的物件。 

`ppNamespace`  
[out]此函式傳回時，收到的指標[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)物件繫結至指定的命名空間。 它設定為指向`null`發生錯誤時。

`impLevel`  
[in]模擬等級。

`authLevel`  
[in]授權層級。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx)方法。

 在預設命名空間中，本機存取`strNetworkResource`可以是簡單的物件路徑:"b>root\default<b"或"\\.\root\default"。 存取遠端電腦上的預設命名空間使用 COM 或 Microsoft 相容的網路功能，包含電腦名稱:"\\myserver\root\default"。 電腦名稱也可以是 DNS 名稱或 IP 位址。 `ConnectServerWmi`函式也可以執行 IPv6 的電腦連線使用 IPv6 位址。

`strUser`不可為空字串。 如果網域中指定了`strAuthority`，它必須不也會包含在`strUser`，或函式會傳回`WBEM_E_INVALID_PARAMETER`。


## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
