---
title: "GetPropertyHandle 函式 （Unmanaged API 參考）"
description: "GetPropertyHandle 函式會傳回該 identies 屬性唯一的控制代碼。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyHandle
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyHandle
helpviewer_keywords: GetPropertyHandle function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3af852fb4b9899a7937f288ffb65d8ca84e4aef1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyhandle-function"></a>GetPropertyHandle 函式
傳回唯一的控制代碼識別屬性。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)執行個體。

`wszPropertyName`  
[in]包含屬性名稱的 UTF16 編碼 characaters null 結尾字串。   

`pType`  
[out]指標[ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx)列舉的成員，表示屬性的 CIM 類型。

`pHandle`   
[out]包含屬性控制代碼的整數指標。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | 找不到指定的屬性名稱。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | 要求的屬性屬於型別是`CIM_OBJECT`或`CIM_ARRAY`。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx)方法。

您可以使用此控制代碼來使用時，識別屬性[IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)方法來讀取或寫入屬性值。

控制代碼可以擷取屬性的所有資料類型以外`CIM_OBJECT`和`CIM_ARRAY`。 傳回類別的所有執行個體的控制代碼的工作。

## <a name="requirements"></a>需求  
**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
