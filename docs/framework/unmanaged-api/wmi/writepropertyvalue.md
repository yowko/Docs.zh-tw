---
title: WritePropertyValue function (Unmanaged API Reference)
description: The WritePropertyValue function writes bytes to a property.
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
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107295"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue function
將指定的位元組數目寫入到屬性控制代碼所指定的屬性中。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```cpp  
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
[in] This parameter is unused.

`ptr`  
[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.

`lHandle`  
[in] An integer that contains the handle that identifies this property. The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.   

`lNumBytes`  
[in] The number of bytes being written to the property. See the [Remarks](#remarks) section for more information.

`pHandle`   
[out] A pointer to the byte array that contains the data.

## <a name="return-value"></a>傳回值

The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | A parameter is not valid. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | A type mismatch occurred. |
|`WBEM_S_NO_ERROR` | 0 | The function call was successful.  |
  
## <a name="remarks"></a>備註

This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.

Use this function to set string and all other non-`DWORD` or non-`QWORD` data.

For nonstring property values, `lNumBytes` must be the correct data size of the property type specified. For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **Header:** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱

- [WMI and Performance Counters (Unmanaged API Reference)](index.md)
