---
title: QualifierSet_Next函數（非託管 API 引用）
description: QualifierSet_Next函數在枚舉中檢索下一個限定詞。
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
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174871"
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

`vFunc`[在]此參數未使用。

`ptr`[在]指向[IWbem 限定詞集實例的](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標。

`lFlags`[在]保留。 此參數必須為 0。

`pstrName`[出]限定詞的名稱。 如果`null`忽略 此 參數，則忽略此參數。否則，`pstrName`不應指向有效`BSTR`或發生記憶體洩漏。 如果不是 null，則函數在返回`BSTR``WBEM_S_NO_ERROR`時始終分配一個新的。

`pVal`[出]成功時，限定詞的值。 如果函數失敗，`VARIANT`則 不修改`pVal`指向 的 。 如果此參數為`null`，則忽略該參數。

`plFlavor`[出]指向接收限定詞味道的 LONG 的指標。 如果不需要風味資訊，則此參數可以是`null`。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 呼叫者未呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可用於開始新的枚舉。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 枚舉中不再保留限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbem 限定詞集的調用：：下一個](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)方法。

重複調用函數`QualifierSet_Next`以枚舉所有限定詞，直到函數返回`WBEM_S_NO_MORE_DATA`。 要提前終止枚舉，請調用[QualifierSet_EndEnumeration](qualifierset-endenumeration.md)函數。

枚舉期間返回的限定詞的順序未定義。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
