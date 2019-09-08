---
title: NextMethod 函式（非受控 API 參考）
description: NextMethod 函數會抓取列舉中的下一個方法。
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee743a4499824bea723043d5a2c7d57d7cbd7106
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798429"
---
# <a name="nextmethod-function"></a>NextMethod 函式
抓取列舉中的下一個方法，其開頭為[BeginMethodEnumeration](beginmethodenumeration.md)的呼叫。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
在未使用此參數。

`ptr`  
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`lFlags`  
[in] 保留。 這個參數必須是0。

`pName`  
脫銷指標， `null`在呼叫之前指向。 當函式傳回時，就是新`BSTR`的位址，其中包含方法名稱。 

`ppSignatureIn`  
脫銷指標，接收[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標，其中包含`in`方法的參數。 

`ppSignatureOut`  
脫銷指標，接收[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標，其中包含`out`方法的參數。 

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有函數的[`BeginEnumeration`](beginenumeration.md)呼叫。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有其他屬性。 |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)方法的呼叫。

呼叫端會藉由呼叫[BeginMethodEnumeration](beginmethodenumeration.md)函數來開始列舉序列，然後呼叫 [NextMethod] 函式，直到函式`WBEM_S_NO_MORE_DATA`傳回為止。 呼叫端（選擇性）呼叫[EndMethodEnumeration](endmethodenumeration.md)來完成序列。 呼叫端可以隨時藉由呼叫[EndMethodEnumeration](endmethodenumeration.md)來終止列舉。

## <a name="example"></a>範例

如需C++範例，請參閱[IWbemClassObject：： NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
