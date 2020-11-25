---
title: 'PutMethod 函式 (非受控 API 參考) '
description: PutMethod 函式會建立方法。
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8edbb8074573b98c017f98197d370c2ad37db80c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726752"
---
# <a name="putmethod-function"></a>PutMethod 函式

建立方法。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a>參數

`vFunc`  
在此參數未使用。

`ptr`  
在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。

`wszName`  
在要建立之方法的名稱。

`lFlags`  
[in] 保留。 此參數必須為0。

`pSignatureIn`  
在 [__Parameters 系統類別](/windows/desktop/WmiSdk/--parameters) 的複本的指標，其中包含 `in` 方法的參數。 如果設定為，則會忽略這個參數 `null` 。  

`pSignatureOut`  
在 [__Parameters 系統類別](/windows/desktop/WmiSdk/--parameters) 的複本的指標，其中包含 `out` 方法的參數。 如果設定為，則會忽略這個參數 `null` 。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數無效。 |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]` *PInSignature* 和 *pOutSignature* 物件中指定的方法參數具有不同的限定詞。
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | 方法參數遺漏 **識別碼** 辨識符號的規格。 |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | 指派給方法參數的識別碼序列不是連續的，也不是從0開始。 |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | 方法的傳回值具有 **識別碼** 辨識符號。 |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | 嘗試從父類別重複使用現有的方法名稱，但簽章不相符。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：:P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) 方法的呼叫。

只有當 `ptr` 是 CIM 類別定義時，才支援這個方法呼叫。 方法操作無法從指向 CIM 實例的 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 指標使用。

使用者無法建立名稱開頭或結尾為底線的方法。 這會保留給系統類別和屬性。

針對方法， `in` 和 `out` 參數會描述為 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 物件中的屬性。

您 `[in/out]` 可以定義參數，方法是將相同的屬性加入至和參數所指向的兩個物件 `pInSignature` `pOutSignature` 。 在此情況下，屬性會共用相同的 **識別碼** 辨識符號值。

除了以外， [__Parameters](/windows/desktop/WmiSdk/--parameters) 類別物件中的每個屬性都 `ReturnValue` 必須有 **識別碼** 辨識符號，此為以零為起始的數值，可識別參數的出現順序。 沒有兩個參數可以有相同的 **識別碼** 值，也不能略過任何 **識別碼** 值。 如果發生任一個條件， `PutMethod` 函數會傳回 `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` 。

## <a name="example"></a>範例

如需範例，請參閱 [IWbemClassObject：:P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) 方法。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
