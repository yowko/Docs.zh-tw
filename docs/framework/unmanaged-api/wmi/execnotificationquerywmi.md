---
title: "ExecNotificationQueryWmi 函式 （Unmanaged API 參考）"
description: "ExecNotificationQueryWmi 函式會執行查詢，以便接收事件。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecNotificationQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecNotificationQueryWmi
helpviewer_keywords: ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f42878c146d478d5183342c3a743f3bd208008b
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi 函式
執行查詢，以接收事件。 呼叫會立即傳回，且呼叫端可以輪詢事件傳回的列舉值到達時。 釋出傳回的列舉值會取消查詢。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

`strQueryLanguage`    
[in]具有 Windows 管理所支援的有效的查詢語言的字串。 它必須是"WQL，「 WMI 查詢語言的縮寫。

`strQuery`  
[in]查詢的文字。 此參數不得為`null`。

`lFlags`   
[in]此函式的行為會影響下列兩個旗標的組合。 這些值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中。 

| 常數 | 值  | 說明  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 如果未設定此旗標，呼叫就會失敗。 這是因為會持續收到的事件，這表示使用者必須輪詢傳回列舉值。 無限期地封鎖此呼叫，可讓，不可能。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 函數會傳回順向的列舉值。 一般而言，順向的列舉程式會更快，並使用較少的記憶體比傳統的列舉值，但不是允許呼叫[複製](clone.md)。 |

`pCtx`  
[in]一般而言，這個值是`null`。 否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)可以提供所要求的事件提供者所使用的執行個體。 

`ppEnum`  
[out]如果沒有發生錯誤，接收列舉值，可讓呼叫端擷取在查詢的結果集的執行個體的指標。 請參閱[備註](#remarks)節的詳細資訊。

`authLevel`  
[in]授權層級。

`impLevel`[in]模擬等級。

`pCurrentNamespace`   
[in]指標[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)物件，代表目前的命名空間。

`strUser`   
[in]使用者名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strPassword`   
[in]密碼。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strAuthority`   
[in]使用者的網域名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有檢視一或多個函式可以傳回的類別權限。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生意外的錯誤。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | 查詢會指定不存在的類別。 |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | 已要求太多有效位數中傳遞的事件。 必須指定較大的輪詢容錯。 |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | 查詢 requess 可以提供比 Windows 管理的詳細資訊。 這`HRESULT`輪詢命名空間中的所有物件的要求中的事件查詢結果時，會傳回。 |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | 查詢中有語法錯誤。 |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | 不支援要求的查詢語言。 |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | 查詢太過複雜。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 是可能已停止和重新啟動。 呼叫[ConnectServerWmi](connectserverwmi.md)一次。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。 |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | 無法剖析查詢。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx)方法。

此函數會傳回之後，呼叫端定期通過傳回`ppEnum`物件[下一步](next.md)函式，以查看是否有任何事件可用。

限制數目`AND`和`OR`可以在 WQL 查詢中使用的關鍵字。 大量的複雜查詢中使用的 WQL 關鍵字可能會導致 WMI 傳回`WBEM_E_QUOTA_VIOLATION`（或 0x8004106c） 錯誤的程式碼做為`HRESULT`值。 多複雜的查詢是取決於 WQL 關鍵字的限制。

如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
