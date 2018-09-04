---
title: SpawnDerivedClass 函式 （Unmanaged API 參考）
description: SpawnDerivedClass 函式會建立新的物件衍生自物件。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04df65a29584f7e2de44389d815b915a541e38f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489795"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass 函式
從指定的物件建立新的衍生類別物件。    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`lFlags`  
[in]保留。 這個參數必須是 0。

`ppNewClass`  
[out]接收新的類別定義物件的指標。 發生錯誤時，新的物件不是傳回，和`ppNewClass`左未經修改。 其值不能是`null`。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | 無效的作業，例如產生類別的執行個體中，已要求。 |
| `WBEM_E_INCOMPLETE_CLASS` | 不完全的來源類別已定義，或向 Windows 管理，因此不允許新的衍生的類別。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` 為 `null`。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)方法。

`ptr` 必須是變成繁衍 （spawn） 物件的父類別的類別定義。 傳回的物件會變成目前物件的子類別。

新的物件中傳回`ppNewClass`會自動變成目前物件的子類別。 無法覆寫這個行為。 沒有任何其他子類別 （衍生類別） 可以建立的方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
