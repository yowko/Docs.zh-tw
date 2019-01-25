---
title: GetPropertyQualifierSet 函式 （Unmanaged API 參考）
description: GetPropertyQualifierSet 函式會擷取為屬性設定的限定詞。
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec91a1f6fba70e3c9706541dc641ddd019d44841
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642200"
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet 函式
擷取特定屬性的限定詞集合。

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
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`wszMethod`  
[in]屬性名稱。 `wszProperty` 必須指向有效`LPCWSTR`。 

`ppQualSet`  
[out]接收的介面指標，可讓您存取屬性的限定詞。 `ppQualSet` 不可以是 `null`。 如果錯誤時，不會傳回新的物件，而指標會設定為指向`null`。 

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | 指定的方法不存在。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數是`null`。 |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | 函式會嘗試取得系統屬性的限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset)方法。 

只有當目前的物件是 CIM 類別定義時，才支援此函式的呼叫。 方法操作不適用於[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters 指向 CIM 執行個體。

因為每一種方法可能有它自己的限定詞[IWbemQualifierSet 指標](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)可讓呼叫端新增、 編輯或刪除這些限定詞。

由於系統內容不有任何限定詞，則函數會傳回`WBEM_E_SYSTEM_PROPERTY`如果您嘗試取得[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標是否為系統屬性。

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱
- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)
