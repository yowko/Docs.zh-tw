---
title: 'NextMethod 函式 (非受控 API 參考) '
description: NextMethod 函式會捕獲列舉中的下一個方法。
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
ms.openlocfilehash: a0466aee47b0a6142870640c78b43f49e221ac2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726765"
---
# <a name="nextmethod-function"></a>NextMethod 函式

以呼叫 [BeginMethodEnumeration](beginmethodenumeration.md)的開頭，抓取列舉中的下一個方法。  

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
在此參數未使用。

`ptr`  
在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。

`lFlags`  
[in] 保留。 此參數必須為0。

`pName`  
擴展指向呼叫之前的指標 `null` 。 當函式傳回時，為包含方法名稱之新的位址 `BSTR` 。

`ppSignatureIn`  
擴展指標，接收包含方法參數之 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 的指標 `in` 。

`ppSignatureOut`  
擴展指標，接收包含方法參數之 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 的指標 `out` 。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有函數的呼叫 [`BeginEnumeration`](beginenumeration.md) 。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有其他屬性。 |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：： NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) 方法的呼叫。

呼叫端會藉由呼叫 [BeginMethodEnumeration](beginmethodenumeration.md) 函式來開始列舉序列，然後呼叫 [NextMethod] 函式，直到函式傳回為止 `WBEM_S_NO_MORE_DATA` 。 （選擇性）呼叫端會藉由呼叫 [EndMethodEnumeration](endmethodenumeration.md)來完成序列。 呼叫端可以在任何時間呼叫 [EndMethodEnumeration](endmethodenumeration.md) ，提早終止列舉。

## <a name="example"></a>範例

如需 c + + 範例，請參閱 [IWbemClassObject：： NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) 方法。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
