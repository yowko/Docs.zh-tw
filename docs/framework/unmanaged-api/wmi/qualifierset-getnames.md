---
title: QualifierSet_GetNames 函式 （Unmanaged API 參考）
description: QualifierSet_GetNames 函式會從物件或屬性擷取限定詞的名稱。
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84059c5e5542e13b1d4fc4efcfc4c7f418db391e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002589"
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames 函式
擷取所有的限定詞或目前的物件或屬性提供的特定限定詞的名稱。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a>參數

`vFunc`   
[in]未使用此參數。

`ptr`   
[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。

`lFlags`   
[in]其中一個下列的旗標或值，指定要包含在列舉中的名稱。

|常數  |值  |描述  |
|---------|---------|---------|
|  | 0 | 傳回所有限定詞的名稱。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 傳回目前的屬性或物件特定限定詞的名稱。 <br/> 屬性： 返回 （包括覆寫） 的屬性特定的辨識符號，並不是這些限定詞會傳播從類別定義。 <br/> 執行個體： 傳回只有特定執行個體的限定詞名稱。 <br/> 類別： 傳回衍生的類別 beiong 特定只限定詞。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 傳回的傳播的限定詞的名稱，從另一個物件。 <br/> 屬性： 傳回的限定詞傳播至這個屬性從類別定義中，而不從本身的屬性。 <br/> 執行個體： 傳回只有這些限定詞會傳播從類別定義。 <br/> 類別： 傳回繼承自父類別的只有這些限定詞的名稱。 |

`pstrNames` [out]新`SAFEARRAY`包含要求的名稱。 陣列可以有 0 的項目。 如果發生錯誤時，新`SAFEARRAY`就不會傳回。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可供開始新的列舉型別。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames)方法。

一旦您已擷取的辨識符號名稱，您可以藉由呼叫依名稱存取每個辨識符號[QualifierSet_Get](qualifierset-get.md)函式。 

它不是發生錯誤，因此擁有零的限定詞，指定物件中的字串數目`pstrNames`在傳回時可能為 0，即使函式會傳回`WBEM_S_NO_ERROR`。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
