---
title: "下一個函式 （Unmanaged API 參考）"
description: "下一個函式 retireves 列舉中的下一個屬性。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e59ef3f65b75a91708dc65f7d4e3d811dc2d3f9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="next-function"></a>下一個函式
擷取列舉開頭的呼叫中的下一個屬性[BeginEnumeration](beginenumeration.md)。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`lFlags`  
[in]保留。 這個參數必須是 0。

`pstrName`  
[out]新`BSTR`，其中包含屬性名稱。 您可以將此參數設定為`null`如果不需要名稱。

`pVal`  
[out]A`VARIANT`填入屬性的值。 您可以將此參數設定為`null`如果不需要值。 如果函數傳回的錯誤碼，`VARIANT`傳遞至`pVal`左未經修改。 

`pvtType`  
[out]指標`CIMTYPE`變數 (`LONG`屬性的型別會放入)。 這個屬性的值可以是`VT_NULL_VARIANT`，在此情況下則需要判斷實際屬性型別。 這個參數也可以是`null`。 

`plFlavor`  
[out]`null`，或接收資訊來源之屬性的值。 請參閱 [備註] 提供可能的值。 

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有不需要呼叫[ `BeginEnumeration` ](beginenumeration.md)函式。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 使用開始新的列舉型別沒有足夠的記憶體。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 遠端程序呼叫之目前處理序和失敗的 Windows 管理。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有其他內容。 |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx)方法。

這個方法也會傳回系統屬性。

如果屬性的基礎類型的物件路徑、 日期或時間或另一種特殊類型，則傳回的類型不包含足夠的資訊。 呼叫端必須檢查`CIMTYPE`指定判斷屬性是否為物件參考、 日期或時間或另一種特殊類型的屬性。

如果`plFlavor`不`null`、`LONG`值接收資訊屬性的原點，如下所示：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準的系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 類別： 屬性繼承自父類別。 </br> 執行個體： 屬性繼承自父類別，而尚未修改的執行個體。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 類別： 屬性屬於衍生的類別。 </br> 執行個體： 執行個體; 所修改的屬性也就是所提供的值，或辨識符號的加入或修改。 |

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
