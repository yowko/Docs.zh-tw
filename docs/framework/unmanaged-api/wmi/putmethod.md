---
title: PutMethod 函式（非受控 API 參考）
description: PutMethod 函數會建立方法。
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
ms.openlocfilehash: 1d409507de593cf198fe87340eece6820eaefc63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127340"
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
在未使用此參數。

`ptr`  
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`wszName`  
在要建立之方法的名稱。 

`lFlags`  
[in] 保留。 這個參數必須是0。

`pSignatureIn`  
在[__Parameters 系統類別](/windows/desktop/WmiSdk/--parameters)複本的指標，其中包含方法的 `in` 參數。 如果設定為 `null`，則會忽略這個參數。  

`pSignatureOut`  
在 [__Parameters 系統類別](/windows/desktop/WmiSdk/--parameters)複本的指標，其中包含方法的 `out` 參數。 如果設定為 `null`，則會忽略這個參數。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數無效。 |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | *PInSignature*和*pOutSignature*物件中指定的 `[in, out]` 方法參數具有不同的限定詞。
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | 方法參數缺少**識別碼**辨識符號的規格。 |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | 指派給方法參數的識別碼系列不是連續的，也不是從0開始。 |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | 方法的傳回值具有**識別碼**辨識符號。 |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | 嘗試重複使用父類別中現有的方法名稱，而且簽章不相符。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：:P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)方法的呼叫。

只有當 `ptr` 是 CIM 類別定義時，才支援這個方法呼叫。 方法操作無法從指向 CIM 實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標使用。

使用者無法建立名稱以底線開頭或結尾的方法。 這會保留給系統類別和屬性。

針對方法，`in` 和 `out` 參數會描述為[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)物件中的屬性。

藉由將相同的屬性新增至 `pInSignature` 和 `pOutSignature` 參數所指向的兩個物件，即可定義 `[in/out]` 參數。 在此情況下，屬性會共用相同的**識別碼**辨識符號值。

`ReturnValue` 以外的[__Parameters](/windows/desktop/WmiSdk/--parameters)類別物件中的每個屬性都必須具有**識別碼**辨識符號，以零為基底的數值，可識別參數出現的順序。 任何兩個參數都不能有相同的**識別碼**值，也無法略過任何**識別碼**值。 如果發生任一種狀況，`PutMethod` 函數會傳回 `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`。

## <a name="example"></a>範例

如需範例，請參閱[IWbemClassObject：:P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
