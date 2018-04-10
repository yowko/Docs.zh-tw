---
title: Get 函式 （Unmanaged API 參考）
description: Get 函式，擷取指定的屬性值。
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69312030689ab1b87e3aadd040395f06e1c94ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="get-function"></a>Get 函式
如果存在的話，擷取指定的屬性值。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`wszName`  
[in]屬性的名稱。

`lFlags`[in]保留。 這個參數必須是 0。

`pVal`[out]如果此函數會傳回成功，則包含值的`wszName`屬性。 `pval`引數指派正確的型別和辨識符號值。

`pvtType`[out]如果此函數會傳回成功，就會包含[CIM 類型常數](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx)，指出此屬性型別。 其值也可以是`null`。 

`plFlavor`[out]如果此函數會傳回成功，接收有關的資訊來源的屬性。 其值可以是`null`，或其中一個定義中的下列 WBEM_FLAVOR_TYPE 常數*WbemCli.h*標頭檔： 

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準的系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 類別： 屬性繼承自父類別。 </br> 執行個體： 屬性繼承自父類別，而尚未修改的執行個體。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 類別： 屬性屬於衍生的類別。 </br> 執行個體： 執行個體; 所修改的屬性也就是所提供的值，或辨識符號的加入或修改。 |

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數都不是有效的。 |
|`WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | 找不到指定的屬性。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx)方法。

`Get`函式也可以傳回系統屬性。

`pVal`引數指派正確的型別和值限定詞和 COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx)函式

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
