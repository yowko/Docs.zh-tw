---
title: 刪除函式 （Unmanaged API 參考）
description: Delete 函式會刪除指定的屬性和所有其限定詞的 CIM 類別定義中。
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7fcf5cff9f95b06a834d73df4090bd1edfca61b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="delete-function"></a>刪除函式
刪除指定的屬性和所有其限定詞的 CIM 類別定義中。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`wszName`  
[in]要刪除之屬性的名稱。 `wszName` 必須是有效的指標`LPCWSTR`。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生意外的錯誤。 |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | 無法刪除屬性。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszzName` 無效。 |
| `WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | 指定的屬性不存在。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 不是記憶體不足，無法完成作業。 |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | 屬性被繼承自基底類別。 |
| `WBEM_E_SYSTEM_PROPERTY` | | 屬性是系統屬性。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | 函式會刪除目前類別的覆寫預設值。 這個屬性的父類別中的預設值已經 reactiviated。 | 

## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx)方法。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
