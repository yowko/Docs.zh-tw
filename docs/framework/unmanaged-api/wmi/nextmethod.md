---
title: NextMethod 函數（非託管 API 引用）
description: NextMethod 函數檢索枚舉中的下一個方法。
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
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174923"
---
# <a name="nextmethod-function"></a>NextMethod 函式
檢索枚舉中的下一個方法，該方法以調用[BeginMethodEa）](beginmethodenumeration.md)開頭。  

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
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`lFlags`  
[in] 保留。 此參數必須為 0。

`pName`  
[出]指向調用`null`之前的指標。 當函數返回時，包含方法名稱的新位址`BSTR`。

`ppSignatureIn`  
[出]接收指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標的指標，其中包含方法的`in`參數。

`ppSignatureOut`  
[出]接收指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標的指標，其中包含方法的`out`參數。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有調用該[`BeginEnumeration`](beginenumeration.md)函數。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 枚舉中沒有更多的屬性。 |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbemClassObject：：NextMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)的調用。

調用方通過調用[BeginMethod 枚舉](beginmethodenumeration.md)函數來開始枚舉序列，然後調用 [NextMethod] 函數，直到函數返回`WBEM_S_NO_MORE_DATA`。 或者，調用方通過調用[EndMethod 枚舉](endmethodenumeration.md)來完成序列。 調用方可以隨時調用[EndMethodEa 枚舉](endmethodenumeration.md)，從而提前終止枚舉。

## <a name="example"></a>範例

有關C++示例，請參閱[IWbemClassObject：：NextMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
