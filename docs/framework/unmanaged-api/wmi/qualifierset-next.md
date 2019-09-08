---
title: QualifierSet_Next 函式（非受控 API 參考）
description: QualifierSet_Next 函數會抓取列舉中的下一個辨識符號。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97a19f236b87a7f4c5b2014aca6ee4abd338c63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798276"
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

`vFunc`   
在未使用此參數。

`ptr`   
在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。

`lFlags`   
[in] 保留。 這個參數必須是0。

`pstrName`   
脫銷辨識符號的名稱。 如果`null`為，則會忽略這個參數， `pstrName`否則不應指向有效`BSTR`的或發生記憶體流失的情況。 如果不是 null，函式`BSTR` `WBEM_S_NO_ERROR`會在傳回時一律配置新的。

`pVal`   
脫銷如果成功，則為限定詞的值。 如果函式失敗，則`VARIANT`不`pVal`會修改所指向的。 如果此參數為`null`，則會忽略參數。

`plFlavor`   
脫銷接收限定詞類別的長整數指標。 如果不需要類別資訊，此參數可以是`null`。 

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 呼叫端未呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可以開始新的列舉。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中不會有更多的限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemQualifierSet：： Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)方法的呼叫。

您會重複`QualifierSet_Next`呼叫函式來列舉所有的限定詞，直到函`WBEM_S_NO_MORE_DATA`式傳回為止。 若要及早終止列舉，請呼叫[QualifierSet_EndEnumeration](qualifierset-endenumeration.md)函數。

列舉期間傳回的限定詞順序未定義。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
