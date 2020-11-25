---
title: 'WritePropertyValue 函式 (非受控 API 參考) '
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
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729404"
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
在此參數未使用。

`ptr`  
在 [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) 實例的指標。

`lHandle`  
在包含識別這個屬性之控制碼的整數。 您可以藉由呼叫 [GetPropertyHandle](getpropertyhandle.md) 函數來抓取控制碼。

`lNumBytes`  
在要寫入屬性的位元組數目。 如需詳細資訊，請參閱「 [備註](#remarks) 」一節。

`pHandle` 擴展包含資料之位元組陣列的指標。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | 發生型別不符。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：： WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) 方法的呼叫。

您可以使用此函數來設定字串和所有其他非 `DWORD` 或非 `QWORD` 資料。

若為非字串屬性值， `lNumBytes` 必須是指定之屬性類型的正確資料大小。 若為字串屬性值， `lNumBytes` 必須是指定之字串的長度（以位元組為單位），而且字串本身必須是偶數長度（以位元組為單位），並以 null 終止字元為開頭。

## <a name="requirements"></a>需求  

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
