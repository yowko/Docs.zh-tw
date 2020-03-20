---
title: 寫入屬性值函數（非託管 API 引用）
description: WritePropertyValue 函數將位元組寫入屬性。
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
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174832"
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
[在]此參數未使用。

`ptr`  
[在]指向[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)實例的指標。

`lHandle`  
[在]包含標識此屬性的控制碼的整數。 可以通過調用[GetPropertyHandle](getpropertyhandle.md)函數來檢索控制碼。

`lNumBytes`  
[在]寫入屬性的位元組數。 有關詳細資訊，請參閱[備註](#remarks)部分。

`pHandle`[出]指向包含資料的位元組陣列的指標。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | 發生型別不符。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數將調用包起來到[IWbemClassObject：：WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)方法。

使用此函數可以設置字串和所有其他非`DWORD`或非`QWORD`資料。

對於非字串屬性值，`lNumBytes`必須為指定的屬性類型的正確資料大小。 對於字串屬性值，`lNumBytes`必須為指定字串的長度（以位元組為單位），並且字串本身的長度（以位元組為單位）並且後面必須使用 null 終止字元。

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
