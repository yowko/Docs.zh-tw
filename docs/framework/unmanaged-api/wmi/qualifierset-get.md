---
title: QualifierSet_Get函數（非託管 API 引用）
description: QualifierSet_Get函數獲取命名的限定詞。
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174884"
---
# <a name="qualifierset_get-function"></a>QualifierSet_Get 函式
取得指定的具名限定詞。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>參數

`vFunc`[在]此參數未使用。

`ptr`[在]指向[IWbem 限定詞集實例的](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標。

`wszName`[在]請求其值的限定詞的名稱。

`lFlags`[在]保留。 此參數必須為 0。

`pVal`[出]成功後，限定詞的正確類型和值。 如果函數失敗，`VARIANT`則 不修改`pVal`指向 的 。 如果此參數為`null`，則忽略該參數。

`plFlavor`[出]指向 LONG 的指標，該指標接收請求的限定詞的限定詞的限定詞風味位。 如果不需要風味資訊，則此參數可以是`null`。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_NOT_FOUND` | 0 x80041002 | 指定的限定詞不存在。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbem 限定詞集的調用：：get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get)方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
