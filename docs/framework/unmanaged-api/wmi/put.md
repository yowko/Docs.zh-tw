---
title: "Put 函式 （Unmanaged API 參考）"
description: "Put 函式會將新值指派給具名屬性。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09d3edc74b34688d5cc36e688f634850cfb60910
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="put-function"></a>Put 函式
將具名的屬性設定為新值。

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
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`wszName`  
[in]屬性的名稱。 此參數不得為`null`。

`lFlags`  
[in]保留。 這個參數必須是 0。

`pVal`   
[in]有效的指標`VARIANT`會變成新的屬性值。 如果`pVal`是`null`或指向`VARIANT`型別的`VT_NULL`，屬性設定為`null`。 

`vtType`  
[in]型別`VARIANT`指向`pVal`。 請參閱[備註](#remarks)節的詳細資訊。
 

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數都不是有效的。 |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | 無法辨識的屬性類型。 建立類別執行個體，如果類別已存在時，會傳回此值。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | 執行個體： 指出`pVal`指向`VARIANT`屬性類型不正確。 <br/> 如需類別定義： 在父類別中，已經有這個屬性和新的 COM 型別是舊的 COM 型別不同。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx)方法。

此函式一律覆寫一個新的目前屬性值。 如果[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)類別定義，會指向`Put`建立或更新屬性值。 當[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)指向 CIM 的執行個體，`Put`更新屬性值;`Put`無法建立屬性值。

`__CLASS`系統屬性時，只可寫入類別建立時，它不能空白。 所有其他的系統屬性是唯讀狀態。

使用者無法建立屬性的名稱以底線 ("_") 開頭或結尾中。 這被保留給系統的類別和屬性。

如果設定的屬性`Put`函式中的父類別，除非屬性類型不符合父類別型別變更屬性的預設值。 如果屬性不存在，而且它不是型別不相符，則屬性會是 ceated。

使用`vtType`參數 CIM 類別定義中建立新屬性時，才與`pVal`是`null`或指向`VARIANT`型別的`VT_NULL`。 在此情況下，`vType`參數會指定屬性的 CIM 類型。 在每個其他情況下，`vtType`必須是 0。 `vtType`如果基礎物件執行個體，則也必須是 0 (即使`Val`是`null`) 因為屬性類型固定的無法變更。   

## <a name="example"></a>範例

如需範例，請參閱[IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx)方法。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
