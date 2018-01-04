---
title: "GetPropertyQualifierSet 函式 （Unmanaged API 參考）"
description: "GetPropertyQualifierSet 函式會擷取針對屬性設定的限定詞。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ca2981c8833abaafd5d206b66d6e91f34e2c91d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet 函式
擷取特定的屬性設定的限定詞。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`wszMethod`  
[in]屬性名稱。 `wszProperty`必須指向有效`LPCWSTR`。 

`ppQualSet`  
[out]接收介面指標，可讓您存取屬性的識別項。 `ppQualSet` 不可以是 `null`。 如果發生錯誤、 沒有傳回新的物件，並將指標設定為指向`null`。 

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
| `WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | 指定的方法不存在。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數是`null`。 |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | 函式會嘗試取得系統屬性的識別項。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx)方法。 

呼叫此函式僅支援目前的物件是 CIM 類別定義。 操作方法不適用於[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters 指向 CIM 執行個體。

因為每個方法可能會有它自己的限定詞， [IWbemQualifierSet 指標](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)可讓呼叫者新增、 編輯或刪除這些限定詞。

由於系統屬性沒有限定詞，則函數會傳回`WBEM_E_SYSTEM_PROPERTY`如果您嘗試取得[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)指標是否為系統屬性。

## <a name="requirements"></a>需求  
**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
