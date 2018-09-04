---
title: ExecQueryWmi 函式 （Unmanaged API 參考）
description: ExecQueryWmi 函式會執行查詢以擷取物件。
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc22edf51cbd726b69dff3da2f0540b2c3864f2e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524477"
---
# <a name="execquerywmi-function"></a>ExecQueryWmi 函式
執行查詢以擷取物件。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExecQueryWmi (
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
[in]具有 Windows 管理所支援的有效的查詢語言的字串。 它必須是 < WQL >，WMI 查詢語言的縮寫字。

`strQuery`  
[in]查詢的文字。 此參數不得為`null`。

`lFlags`   
[in]旗標的組合會影響此函式的行為。 下列的值會定義於*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼： 

| 常數 | 值  | 描述  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果集、 函式會擷取已修改儲存在目前連接的地區設定當地語系化的命名空間中的限定詞。 <br/> 如果沒有設定，此函數會擷取立即的命名空間中儲存的辨識符號。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會導致半同步呼叫。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 函數會傳回順向的列舉值。 一般而言，順向的列舉值會比較快，並使用較少的記憶體，比傳統的列舉值，但不是允許呼叫[複製品](clone.md)。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | 之前在發行時，WMI 就會保留在 enumration 物件的指標。 | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | 可確保任何傳回的物件方式，有足夠的資訊，因此該系統屬性，例如 **__PATH**， **__RELPATH**，並 **__SERVER**，不是`null`。 |
| `WBEM_FLAG_PROTOTYPE` | 2 | 這個旗標用於原型設計。 它不會執行查詢，並改為傳回 看起來像一般的結果物件的物件。 |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | 原因直接存取提供者的指定，而不考慮其父類別或任何子類別的類別。 |

建議的旗標`WBEM_FLAG_RETURN_IMMEDIATELY`和`WBEM_FLAG_FORWARD_ONLY`為了達到最佳效能。

`pCtx`  
[in]一般而言，這個值是`null`。 否則，它是指標[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)可用的提供者所提供的要求的類別的執行個體。 

`ppEnum`  
[out]如果未發生錯誤，接收列舉值，可讓呼叫端擷取查詢的結果集中的執行個體的指標。 查詢可以有具有零的執行個體的結果集。 請參閱[備註](#remarks)節的詳細資訊。

`authLevel`  
[in]授權層級。

`impLevel` [in]模擬等級。

`pCurrentNamespace`   
[in]指標[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件，表示目前的命名空間。

`strUser`   
[in]使用者名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strPassword`   
[in]密碼。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strAuthority`   
[in]使用者的網域名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有檢視一個或多個函式會傳回類別的權限。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | 查詢必須有語法錯誤。 |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | 不支援要求的查詢語言。 |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | 查詢太過複雜。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 是可能已停止和重新啟動。 呼叫[ConnectServerWmi](connectserverwmi.md)一次。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。 |
| `WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | 查詢指定了不存在的類別。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery)方法。

此函式會處理查詢中指定`strQuery`參數，並建立呼叫者可以透過它存取查詢結果的列舉值。 列舉值是一個指向[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)介面; 查詢結果會透過提供的類別物件的執行個體[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)介面。

有一些限制的數目`AND`和`OR`可用在 WQL 查詢的關鍵字。 大量複雜的查詢中所使用的 WQL 關鍵字可能會導致傳回 WMI `WBEM_E_QUOTA_VIOLATION` （或 0x8004106c） 做為錯誤碼`HRESULT`值。 複雜的查詢會視 WQL 關鍵字的限制。

如果函式呼叫失敗，您可以藉由呼叫來取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
