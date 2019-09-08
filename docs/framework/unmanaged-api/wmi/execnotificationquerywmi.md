---
title: ExecNotificationQueryWmi 函式（非受控 API 參考）
description: ExecNotificationQueryWmi 函數會執行查詢來接收事件。
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cfe54c7c9b7ae707b2d3591afbd830bac171f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798640"
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi 函式

執行查詢以接收事件。 此呼叫會立即傳回，而且呼叫端可以在事件抵達時輪詢傳回的列舉值。 釋放傳回的列舉值會取消查詢。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
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

`strQueryLanguage`\
在具有 Windows 管理支援之有效查詢語言的字串。 它必須是 "WQL"，也就是 WMI 查詢語言的縮寫。

`strQuery`\
在查詢的文字。 這個參數不可以是 `null`。

`lFlags`\
在下列兩個旗標的組合，會影響此函式的行為。 這些值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數。

| 常數 | 值  | 描述  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 如果未設定此旗標，呼叫將會失敗。 這是因為系統會持續收到事件，這表示使用者必須輪詢傳回的列舉值。 無限期地封鎖此呼叫會導致無法這麼做。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 函數會傳回順向列舉值。 一般來說，順向列舉值的速度較快，而且使用的記憶體比傳統的列舉值少，但它們不允許[複製](clone.md)的呼叫。 |

`pCtx`\
在通常，此值為`null`。 否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求事件的提供者使用。

`ppEnum`\
脫銷如果沒有發生錯誤，則會接收列舉值的指標，允許呼叫者抓取查詢結果集中的實例。 如需詳細資訊，請參閱[備註](#remarks)一節。

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
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | 查詢指定了不存在的類別。 |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | 要求傳遞事件的精確度太高。 必須指定較大的輪詢容錯。 |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | 查詢要求的資訊比 Windows 管理所能提供的還要多。 當`HRESULT`事件查詢產生輪詢命名空間中所有物件的要求時，就會傳回此專案。 |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | 查詢發生語法錯誤。 |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | 不支援要求的查詢語言。 |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | 查詢太複雜。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 可能已停止並重新啟動。 再次呼叫[ConnectServerWmi](connectserverwmi.md) 。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。 |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | 無法剖析查詢。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemServices：： ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery)方法的呼叫。

函式傳回之後，呼叫端會定期將傳回`ppEnum`的物件傳遞至[下一個](next.md)函式，以查看是否有任何可用的事件。

可以在 WQL 查詢中使用的`AND`和`OR`關鍵字數目有所限制。 複雜查詢中使用的大量 WQL 關鍵字可能會使 WMI `WBEM_E_QUOTA_VIOLATION`傳回（或0x8004106c）錯誤碼`HRESULT`做為值。 WQL 關鍵字的限制取決於查詢的複雜程度。

如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
