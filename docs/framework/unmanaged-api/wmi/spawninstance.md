---
title: SpawnInstance 函式（非受控 API 參考）
description: SpawnInstance 函數會建立類別的新實例。
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
ms.openlocfilehash: f93b4fbd5429ed2bdae8fb707e61df024cd8fd6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107519"
---
# <a name="spawninstance-function"></a>SpawnInstance 函式
建立類別的新執行個體。    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>參數

`vFunc`  
在未使用此參數。

`ptr`  
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`lFlags`  
[in] 保留。 這個參數必須是0。

`ppNewInstance`  
脫銷接收類別之新實例的指標。 如果發生錯誤，則不會傳回新的物件，`ppNewInstance` 會保留不修改的狀態。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` 不是有效的類別定義，因此無法產生新的實例。 可能是未完成，或未透過呼叫[PutClassWmi](putclasswmi.md)向 Windows 管理註冊。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` 為 `null`。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)方法的呼叫。

`ptr` 必須是從 Windows 管理取得的類別定義。 （請注意，支援從實例產生實例，但傳回的實例是空的）。接著，您可以使用此類別定義來建立新的實例。 如果您想要將實例寫入 Windows 管理，則需要呼叫[PutInstanceWmi](putinstancewmi.md)函數。

在 `ppNewClass` 中傳回的新物件會自動成為目前物件的子類別。 無法覆寫此行為。 沒有其他方法可建立子類別（衍生類別）。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
