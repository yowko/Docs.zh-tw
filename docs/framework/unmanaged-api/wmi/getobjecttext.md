---
title: 獲取物件文本功能（非託管 API 引用）
description: GetObjectText 函數在 MOF 語法中返回物件的文本呈現。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176782"
---
# <a name="getobjecttext-function"></a>GetObjectText 函式
在管理物件格式 （MOF） 語法中返回物件的文本呈現。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`lFlags`  
[在]通常為 0。 如果`WBEM_FLAG_NO_FLAVORS`指定 （或 0x1），則包含限定詞而不包含傳播或風味資訊。

`pstrObjectText`[出]指向上條目的`null`指標。 返回時，包含物件的`BSTR`MOF 語法呈現的新分配。  

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 出現了一個普遍的失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數將調用包起來到[IWbem ClassObject：：getObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)方法。

返回的 MOF 文本不包含有關物件的所有資訊，但僅包含足夠的資訊，以便 MOF 編譯器能夠重新創建原始物件。 例如，不包含傳播的限定詞或父類屬性。

以下演算法用於重建方法參數的文本：

1. 參數按其識別碼值的順序重新排序。
1. 指定為`[in]`並`[out]`組合到單個參數的參數。

`pstrObjectText`調用函數時必須指向`null`的 指標;它不得指向方法調用之前有效的字串，因為指標不會被處理。

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
