---
title: PutMethod 函式 （Unmanaged API 參考）
description: PutMethod 函式建立的方法。
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cdf34ff6ae506ba209300685da3752820b250a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516746"
---
# <a name="putmethod-function"></a>PutMethod 函式
建立方法。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`wszName`  
[in]若要建立方法的名稱。 

`lFlags`  
[in]保留。 這個參數必須是 0。

`pSignatureIn`  
[in]指標，一份[__Parameters 系統類別](/windows/desktop/WmiSdk/--parameters)包含`in`方法的參數。 如果會忽略這個參數設定為`null`。  

`pSignatureOut`  
[in] 指標，一份[__Parameters 系統類別](/windows/desktop/WmiSdk/--parameters)包含`out`方法的參數。 如果會忽略這個參數設定為`null`。
 

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 找不到有效的一或多個參數。 |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]`方法中指定的參數*pInSignature*並*pOutSignature*物件有不同的限定詞。
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | 方法參數遺漏的規格**識別碼**限定詞。 |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | 指派給方法參數的識別碼數列不連續，或無法啟動為 0。 |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | 方法的傳回值具有**識別碼**限定詞。 |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | 嘗試重複使用現有的方法名稱自父類別，並且簽章不符。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)方法。

這個方法呼叫時才支援`ptr`為 CIM 類別定義。 方法操作不是可從[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)指向 CIM 執行個體的指標。

使用者無法建立方法，名稱開頭或結尾加上底線。 這被保留給系統的類別和屬性。

對於方法而言`in`並`out`參數會被稱為中的屬性[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)物件。

`[in/out]`參數可以將相同的屬性新增至所指的這兩個物件定義`pInSignature`和`pOutSignature`參數。 在此情況下，屬性會共用相同**識別碼**辨識符號值。

中的每一個屬性[__Parameters](/windows/desktop/WmiSdk/--parameters)以外的其他類別物件`ReturnValue`必須**識別碼**限定詞、 以零為起始的數字值，識別參數出現的順序。 任何兩個參數可以具有相同**識別碼**的值，但不含任何**識別碼**可略過的值。 如果其中一個條件發生時，`PutMethod`函式會傳回`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`。

## <a name="example"></a>範例

如需範例，請參閱[IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
