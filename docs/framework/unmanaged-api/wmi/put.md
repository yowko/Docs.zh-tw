---
title: Put 函式 （Unmanaged API 參考）
description: Put 函式會將新的值指派給具名屬性。
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec8fe889885b555cbf9a95cd34b7330efff27f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43460981"
---
# <a name="put-function"></a>Put 函式
設定具名的屬性，為新值。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`wszName`  
[in]屬性的名稱。 此參數不得為`null`。

`lFlags`  
[in]保留。 這個參數必須是 0。

`pVal`   
[in]有效的指標`VARIANT`會變成新的屬性值。 如果`pVal`是`null`或指向`VARIANT`型別的`VT_NULL`，屬性設定為`null`。 

`vtType`  
[in]型別`VARIANT`所指向`pVal`。 請參閱[備註](#remarks)節的詳細資訊。
 

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 找不到有效的一或多個參數。 |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | 無法辨識的屬性型別。 建立類別執行個體，如果類別已存在時，會傳回此值。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | 執行個體： 表示`pVal`指向`VARIANT`屬性的型別不正確。 <br/> 如需類別定義： 在父類別中，已經存在的屬性和新的 COM 型別是從舊的 COM 型別不同。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)方法。

此函式一律覆寫一個新的目前屬性值。 如果[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向類別定義，`Put`建立或更新的屬性值。 當[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向 CIM 的執行個體，`Put`更新屬性值;`Put`無法建立屬性的值。

`__CLASS`系統屬性時，只可寫入類別在建立期間，它可能不能空白。 所有其他的系統屬性是唯讀的。

使用者無法建立屬性，其開頭或結尾底線 ("_") 的名稱。 這被保留給系統的類別和屬性。

如果設定的屬性`Put`函式父類別中，屬性的預設值已變更，除非屬性型別不符的父類別型別。 如果屬性不存在，而且它不是類型不符，則屬性會是 visio 建立。

使用`vtType`只有在 CIM 類別定義中建立新的屬性時的參數和`pVal`是`null`或指向`VARIANT`型別的`VT_NULL`。 在此情況下，`vType`參數指定之屬性的 CIM 型別。 在每個其他情況下，`vtType`必須是 0。 `vtType` 如果基礎的物件執行個體，則也必須是 0 (即使`Val`是`null`) 因為屬性的型別固定的無法變更。   

## <a name="example"></a>範例

如需範例，請參閱[IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
