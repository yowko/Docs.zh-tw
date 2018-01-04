---
title: "SpawnInstance 函式 （Unmanaged API 參考）"
description: "SpawnInstance 函式會建立類別的新執行個體。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SpawnInstance
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SpawnInstance
helpviewer_keywords: SpawnInstance function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 68508f3000e7f4ac481f940ef4c715366c37125c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="spawninstance-function"></a>SpawnInstance 函式
建立類別的新執行個體。    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`lFlags`  
[in]保留。 這個參數必須是 0。

`ppNewInstance`  
[out]接收此類別的新執行個體的指標。 如果發生錯誤時，新的物件不是傳回，和`ppNewInstance`左未經修改。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`不是有效的類別定義，並無法繁衍 （spawn） 的新執行個體。 可能是不完整，或是它尚未註冊使用 Windows Management 藉由呼叫[PutClassWmi](putclasswmi.md)。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` 為 `null`。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx)方法。

`ptr`必須是類別定義取自 Windows 管理。 （請注意，支援繁衍 （spawn） 從執行個體的執行個體，但傳回的執行個體是空的）。然後，您會使用此類別定義來建立新的執行個體。 呼叫[PutInstanceWmi](putinstancewmi.md)功能是必要的如果您想要寫入 Windows 管理中的執行個體。




新的物件中傳回`ppNewClass`會自動變成目前物件的子類別。 無法覆寫這個行為。 沒有任何子類別 （衍生的類別） 可以建立的方法。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
