---
title: PutClassWmi 函式（非受控 API 參考）
description: PutClassWmi 函數會建立新的類別，或更新現有的類別。
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
ms.openlocfilehash: 7fcf879705135e0093868b48580a37f9d46aa594
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798388"
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
在有效類別定義的指標。 必須使用所有必要的屬性值正確地初始化。

`lFlags`\
在會影響此函式行為的旗標組合。 下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果設定，WMI 不會將任何限定詞儲存為修改過的類別。 <br> 如果未設定，則會假設此物件未當地語系化，而且所有限定詞都會與這個實例一起儲存。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 如果類別不存在，請建立它，如果已存在，則予以覆寫。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | 更新類別。 類別必須存在，呼叫才會成功。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | 建立類別。 如果類別已經存在，呼叫就會失敗。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | 呼叫`PutClassWmi`時，推播提供者必須指定此旗標，以指出這個類別已變更。 |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | 如果沒有衍生類別，而且沒有該類別的實例，則允許更新類別。 如果變更僅限於不重要的限定詞（例如描述辨識符號），它也可讓您在所有情況下進行更新。 如果類別有實例或變更為重要的限定詞，則更新會失敗。 |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | 即使有子類別，也允許更新類別，但前提是變更不會造成與子類別的任何衝突。 例如，此旗標可讓新的屬性新增至先前未在任何子類別中提及的基類。 如果類別有實例，則更新會失敗。 |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | 當存在衝突的子類別時，強制更新類別。 例如，如果在子類別中定義了類別限定詞，而且基類嘗試加入與現有的限定詞衝突，則此旗標會強制更新。 在強制模式中，會藉由刪除子類別中衝突的限定詞來解決 tis 衝突。 |

`pCtx`\
在通常，此值為`null`。 否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求之類別的提供者使用。

`ppCallResult`\
脫銷如果`null`為，則不會使用這個參數。 如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY` ，`WBEM_S_NO_ERROR`則函式會立即傳回。 `ppCallResult` 參數會接收新 [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) 物件的指標。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有建立或修改類別的許可權。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | 指定的類別無效。 一般而言，這表示會`pObject`指定實例物件。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | 指定的類別名稱無效。 |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | 嘗試進行會使子類別失效的變更。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | 已`WBEM_FLAG_CREATE_ONLY`指定旗標，但類別已經存在。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`在中`lFlags`指定了，而且找不到類別。 |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | 尚未設定類別的必要屬性。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 可能已停止並重新啟動。 再次呼叫[ConnectServerWmi](connectserverwmi.md) 。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemServices：:P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass)方法的呼叫。

使用者不得以底線字元來建立名稱開頭或結尾的類別。

如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
