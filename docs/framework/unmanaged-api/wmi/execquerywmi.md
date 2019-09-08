---
title: ExecQueryWmi 函式（非受控 API 參考）
description: ExecQueryWmi 函數會執行查詢來抓取物件。
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
ms.openlocfilehash: b8547d306819e85b838f1160d9912dd43e42f2f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798683"
---
# <a name="execquerywmi-function"></a>ExecQueryWmi 函式

執行查詢以擷取物件。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
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

`strQueryLanguage`\
在具有 Windows 管理支援之有效查詢語言的字串。 它必須是 "WQL"，也就是 WMI 查詢語言的縮寫。

`strQuery`\
在查詢的文字。 這個參數不可以是 `null`。

`lFlags`\
在會影響此函式行為的旗標組合。 下列值定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

| 常數 | 值  | 描述  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果設定，函式會抓取已修改的限定詞，並儲存在目前連接地區設定的當地語系化命名空間中。 <br/> 如果未設定，此函式只會抓取立即命名空間中儲存的限定詞。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 函數會傳回順向列舉值。 一般來說，順向列舉值的速度較快，而且使用的記憶體比傳統的列舉值少，但它們不允許[複製](clone.md)的呼叫。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI 會保留列舉中物件的指標，直到釋放它們為止。 |
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | 確保任何傳回的物件都有足夠的資訊，因此系統屬性（例如 **__PATH**、 **__RELPATH**和 **__SERVER**）不`null`會。 |
| `WBEM_FLAG_PROTOTYPE` | 2 | 此旗標用於原型設計。 它不會執行查詢，而是會傳回看起來像一般結果物件的物件。 |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | 會針對指定的類別直接存取提供者，而不考慮其父類別或任何子類別。 |

建議的旗標`WBEM_FLAG_RETURN_IMMEDIATELY`為`WBEM_FLAG_FORWARD_ONLY` ，以達到最佳效能。

`pCtx`\
在通常，此值為`null`。 否則，它是[IWbemCoNtext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)實例的指標，可供提供所要求之類別的提供者使用。

`ppEnum`\
脫銷如果沒有發生錯誤，則會接收列舉值的指標，允許呼叫者抓取查詢結果集中的實例。 查詢的結果集可以有零個實例。 如需詳細資訊，請參閱[備註](#remarks)一節。

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

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有許可權可查看函數可以傳回的一個或多個類別。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | 查詢發生語法錯誤。 |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | 不支援要求的查詢語言。 |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | 查詢太複雜。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 可能已停止並重新啟動。 再次呼叫[ConnectServerWmi](connectserverwmi.md) 。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | 查詢指定了不存在的類別。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemServices：： ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery)方法的呼叫。

此函式會處理`strQuery`參數中指定的查詢，並建立可供呼叫端用來存取查詢結果的列舉值。 列舉值是指向[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)介面的指標;查詢結果是透過[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)介面提供之類別物件的實例。

可以在 WQL 查詢中使用的`AND`和`OR`關鍵字數目有所限制。 複雜查詢中使用的大量 WQL 關鍵字可能會使 WMI `WBEM_E_QUOTA_VIOLATION`傳回（或0x8004106c）錯誤碼`HRESULT`做為值。 WQL 關鍵字的限制取決於查詢的複雜程度。

如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
