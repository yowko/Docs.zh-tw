---
title: WritePropertyValue 函式（非受控 API 參考）
description: WritePropertyValue 函數會將位元組寫入至屬性。
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
ms.openlocfilehash: a3c42129835f9b30bed493a0992d49d7e2a458e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798178"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue 函式
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
在未使用此參數。

`ptr`  
在[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)實例的指標。

`lHandle`  
在整數，包含識別這個屬性的控制碼。 呼叫[GetPropertyHandle](getpropertyhandle.md)函式可以抓取控制碼。   

`lNumBytes`  
在要寫入屬性的位元組數目。 如需詳細資訊，請參閱[備註](#remarks)一節。

`pHandle`   
脫銷包含資料之位元組陣列的指標。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | 發生類型不符。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)方法的呼叫。

使用此函式可設定字串和所有其他非`DWORD`或`QWORD`非資料。

針對非字串屬性值， `lNumBytes`必須是指定之屬性類型的正確資料大小。 對於字串屬性值， `lNumBytes`必須是指定之字串的長度（以位元組為單位），而字串本身必須是長度（以位元組為單位），且後面接著 null 終止字元。

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
