---
title: PutClassWmi 函式 （Unmanaged API 參考）
description: PutClassWmi 函式會建立新的類別，或更新現有的。
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422de614d2e2ddb93cc1e932a8672e1e8269b2c0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636651"
---
# <a name="putclasswmi-function"></a>PutClassWmi 函式

建立新類別或更新現有類別。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>參數

`pObject`\
[in]有效的類別定義的指標。 它必須具有所有必要的屬性值正確初始化。

`lFlags`\
[in]旗標的組合會影響此函式的行為。 下列的值會定義於*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果設定，WMI 不會儲存任何限定詞以修改過的類別。 <br> 如果沒有設定，系統會假設此物件不會進行當地語系化，，而且所有的限定詞會儲存與這個執行個體。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 如果不存在，或是如果它已經存在，覆寫它，請建立的類別。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | 更新類別。 此類別必須存在，呼叫才會成功。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | 建立的類別。 如果類別已存在，則呼叫會失敗。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會導致半同步呼叫。 |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | 推入提供者在呼叫時，必須指定這個旗標`PutClassWmi`表示此類別已變更。 |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | 允許類別如果有任何衍生的類別和該類別的執行個體不會更新。 它也可讓更新在所有情況下如果只是變更並不重要的辨識符號，例如描述限定詞。 如果類別具有執行個體或變更重要的限定詞，則更新失敗。 |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | 即使有子類別，只要變更不會發生任何衝突造成與子類別，可讓更新的類別。 比方說，這個旗標可讓新的屬性，可以加入至先前未提及的任何子類別的基底類別。 如果該類別的執行個體，則更新失敗。 |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | 衝突的子類別存在時，會強制更新類別。 比方說，這個旗標會強制更新如果類別限定詞定義在子類別，而基底類別會嘗試將相同的辨識符號與現有的衝突。 在強制模式中，本衝突的解決方式刪除衝突的辨識符號中的子類別。 |

`pCtx`\
[in]一般而言，這個值是`null`。 否則，它是指標[IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)可用的提供者所提供的要求的類別的執行個體。

`ppCallResult`\
[out]如果`null`，不使用這個參數。 如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY`，此函式會立即傳回並`WBEM_S_NO_ERROR`。 `ppCallResult`參數會接收到新的指標[IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult)物件。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有建立或修改類別的權限。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | 指定的類別不是有效的。 一般而言，這表示`pObject`指定的執行個體物件。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | 指定的類別名稱無效。 |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | 您嘗試進行的變更，可能會導致失效的子類別。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY`指定旗標，但是類別已存在。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` 中指定了`lFlags`，而且找不到類別。 |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | 類別的必要的屬性不是所有已設定。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 是可能已停止和重新啟動。 呼叫[ConnectServerWmi](connectserverwmi.md)一次。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass)方法。

使用者可能無法建立類別開頭或結尾底線字元的名稱。

如果函式呼叫失敗，您可以藉由呼叫來取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)
