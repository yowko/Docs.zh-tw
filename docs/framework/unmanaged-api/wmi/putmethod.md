---
title: "PutMethod 函式 （Unmanaged API 參考）"
description: "PutMethod 函式建立的方法。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e97ffcf44a738234f67d9736382c46c42e5b61e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`wszName`  
[in]若要建立方法的名稱。 

`lFlags`  
[in]保留。 這個參數必須是 0。

`pSignatureIn`  
[in]指標，一份[__Parameters 系統類別](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)包含`in`方法的參數。 如果，則會忽略這個參數設定為`null`。  

`pSignatureOut`  
[in] 指標，一份[__Parameters 系統類別](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)包含`out`方法的參數。 如果，則會忽略這個參數設定為`null`。
 

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數都不是有效的。 |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]`方法參數中指定*pInSignature*和*pOutSignature*物件具有不同的辨識符號。
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | 方法參數遺漏的規格**識別碼**限定詞。 |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | 指派給方法參數的識別碼數列不連續或沒有不會從 0 開始。 |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | 方法的傳回值具有**識別碼**限定詞。 |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | 嘗試將重複使用現有的方法名稱自父類別，並且簽章不符。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx)方法。

這個方法呼叫時才支援`ptr`為 CIM 類別定義。 方法操作中未提供[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)指向 CIM 執行個體的指標。

使用者無法建立方法以底線開頭或結尾的名稱。 這被保留給系統的類別和屬性。

一種方法，如`in`和`out`參數說明中做為屬性[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)物件。

`[in/out]`參數可由相同的屬性加入至這兩個所指向的物件定義`pInSignature`和`pOutSignature`參數。 在此情況下，內容會共用相同**識別碼**辨識符號值。

中的每一個屬性[__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)以外類別物件`ReturnValue`必須**識別碼**辨識符號，以零為起始的數字值，識別這些參數會顯示的順序。 任何兩個參數可以具有相同**識別碼**值，且沒有**識別碼**略過的值。 如果發生其中一個條件，`PutMethod`函式會傳回`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`。

## <a name="example"></a>範例

如需範例，請參閱[IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx)方法。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
