---
title: SpawnInstance 函式 （Unmanaged API 參考）
description: SpawnInstance 函式會建立類別的新執行個體。
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8056ef18089f56f1f9b6717d505fa3d058957541
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074413"
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
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`lFlags`  
[in] 保留。 這個參數必須是 0。

`ppNewInstance`  
[out]接收此類別的新執行個體的指標。 發生錯誤時，新的物件不是傳回，和`ppNewInstance`左未經修改。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` 不是有效的類別定義，並無法繁衍 （spawn） 的新執行個體。 已完成，或它尚未註冊使用 Windows Management 藉由呼叫[PutClassWmi](putclasswmi.md)。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` 是`null`。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)方法。

`ptr` 必須在類別定義取得從 Windows 管理。 （請注意，支援繁衍的執行個體從執行個體，但傳回的執行個體是空的）。然後，您會使用此類別定義來建立新的執行個體。 呼叫[PutInstanceWmi](putinstancewmi.md)函式是必要的如果您想要撰寫 Windows 管理的執行個體。

新的物件中傳回`ppNewClass`會自動變成目前物件的子類別。 無法覆寫這個行為。 沒有任何其他子類別 （衍生類別） 可以建立的方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
