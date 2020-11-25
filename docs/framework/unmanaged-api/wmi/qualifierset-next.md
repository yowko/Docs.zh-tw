---
title: 'QualifierSet_Next 函式 (非受控 API 參考) '
description: QualifierSet_Next 函式會捕獲列舉中的下一個限定詞。
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 54d79a3dc081e9cdcb42153b6f7aa457557e3399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721123"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next 函式

擷取透過呼叫 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 函式而開始之列舉中的下一個限定詞。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>參數

`vFunc` 在此參數未使用。

`ptr` 在 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 實例的指標。

`lFlags` 在保留。 此參數必須為0。

`pstrName` 擴展限定詞的名稱。 如果為 `null` ，則會忽略這個參數，否則 `pstrName` 不應指向有效 `BSTR` 或記憶體流失的情況。 如果不是 null，則函式會在傳回時一律配置新的 `BSTR` `WBEM_S_NO_ERROR` 。

`pVal` 擴展成功時，辨識符號的值。 如果函式失敗，則 `VARIANT` `pVal` 不會修改指向的。 如果此參數為 `null` ，則會忽略參數。

`plFlavor` 擴展收到限定詞類別的 LONG 指標。 如果不需要類別資訊，這個參數可以是 `null` 。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 呼叫端未呼叫 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可用來開始新的列舉。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有剩餘的限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemQualifierSet：： Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) 方法的呼叫。

您可以重複呼叫函式 `QualifierSet_Next` 來列舉所有的限定詞，直到函數傳回為止 `WBEM_S_NO_MORE_DATA` 。 若要提早終止列舉，請呼叫 [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) 函數。

列舉期間傳回的限定詞順序未定義。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
