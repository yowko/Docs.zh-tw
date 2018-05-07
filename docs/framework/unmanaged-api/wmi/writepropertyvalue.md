---
title: WritePropertyValue 函式 （Unmanaged API 參考）
description: WritePropertyValue 函式會將位元組寫入屬性。
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6aafb918616d27cf6289a8747f3336b2e813beb6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue 函式
寫入屬性控制代碼所識別的屬性中指定的位元組數目。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)執行個體。

`lHandle`  
[in]整數，其中包含識別這個屬性的控制代碼。 控制代碼可以藉由呼叫擷取[GetPropertyHandle](getpropertyhandle.md)函式。   

`lNumBytes`  
[in]要寫入屬性的位元組數目。 請參閱[備註](#remarks)節的詳細資訊。

`pHandle`   
[out]包含資料的位元組陣列指標。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | 發生類型不符。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx)方法。

使用此函式來設定字串和所有其他非`DWORD`或非-`QWORD`資料。

如需非字串屬性值，`lNumBytes`必須是正確的資料大小，指定型別的屬性。 字串屬性值，`lNumBytes`必須是長度以位元組為單位，指定的字串和字串本身，以位元組為單位的平均長度必須是和遵循以 null 結束的字元。

## <a name="requirements"></a>需求  
**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
