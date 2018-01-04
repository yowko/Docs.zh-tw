---
title: "QualifierSet_Put 函式 （Unmanaged API 參考）"
description: "QualifierSet_Put 函式會寫入具名的辨識符號和它的值。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Put
helpviewer_keywords: QualifierSet_Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bf5c6dbf0f707942d58f4d7cf155636f0532724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put 函式
寫入具名的辨識符號和值。 新限定詞會覆寫先前同名的值。 如果不存在限定詞，則會建立它。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a>參數

`vFunc`   
[in]未使用這個參數。

`ptr`   
[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。

`wszName`   
[in]要寫入的限定詞的名稱。

`pVal`[in]有效的指標`VARIANT`，其中包含要寫入的限定詞。 此參數不得為`null`。

`lFlavor`[in]下列常數，定義所需的限定詞標註，這個辨識符號的其中一個。 預設值是`WBEM_FLAVOR_OVERRIDABLE`(0)。

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | 限定詞會覆寫衍生的類別或執行個體中。 **這是預設值。** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | 限定詞會傳播到執行個體。 |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | 限定詞會傳播到衍生的類別。 |
| ' WBEM_FLAVOR_NOT_OVERRIDABLE | 0x10 | 無法在衍生類別或執行個體中覆寫限定詞。 |
| ' WBEM_FLAVOR_AMENDED | 0x80 | 限定詞已經過當地語系化。 |

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | 曾不合法嘗試指定**金鑰**不得為索引鍵屬性上的限定詞。 指定索引鍵 om c，則為物件的協助定義，且無法變更針對每個執行個體。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal`參數不是合法的限定詞類型。 |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | 不可能呼叫`QualifierSet_Put`限定詞的方法，因為主控物件不允許覆寫。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx)方法。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
