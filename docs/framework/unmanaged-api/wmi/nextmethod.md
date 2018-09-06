---
title: NextMethod 函式 （Unmanaged API 參考）
description: NextMethod 函式會擷取下一個方法，列舉型別。
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
ms.openlocfilehash: 1d019c67849197cd24171ff607e60e9f08d5ff70
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44040872"
---
# <a name="nextmethod-function"></a>NextMethod 函式
擷取開頭呼叫列舉中的下一步 方法[BeginMethodEnumeration](beginmethodenumeration.md)。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
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
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`lFlags`  
[in]保留。 這個參數必須是 0。

`pName`  
[out]指標指向`null`在呼叫之前。 當函式傳回時，新的位址`BSTR`，其中包含方法名稱。 

`ppSignatureIn`  
[out]收到的指標的指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)包含`in`方法的參數。 

`ppSignatureOut`  
[out]收到的指標的指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)包含`out`方法的參數。 

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有不需要呼叫[ `BeginEnumeration` ](beginenumeration.md)函式。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有更多的屬性。 |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)方法。

呼叫者藉由呼叫開始列舉型別序列[BeginMethodEnumeration](beginmethodenumeration.md)函式，然後再呼叫 [NextMethod] 函式，直到函式會傳回`WBEM_S_NO_MORE_DATA`。 呼叫端 （選擇性） 藉由呼叫完成序列[EndMethodEnumeration](endmethodenumeration.md)。 呼叫端可能會提早終止列舉型別，藉由呼叫[EndMethodEnumeration](endmethodenumeration.md)在任何時間。

## <a name="example"></a>範例

如需 c + + 範例，請參閱 < [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
