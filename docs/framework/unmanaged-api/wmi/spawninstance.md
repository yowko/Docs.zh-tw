---
title: 'SpawnInstance 函式 (非受控 API 參考) '
description: SpawnInstance 函式會建立類別的新實例。
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
ms.openlocfilehash: 176bc83dd02381af8c2bc3995a37e7fee7c1bebf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732225"
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
在此參數未使用。

`ptr`  
在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。

`lFlags`  
[in] 保留。 此參數必須為0。

`ppNewInstance`  
擴展接收類別新實例的指標。 如果發生錯誤，則不會傳回新的物件，而且 `ppNewInstance` 會保持未修改狀態。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` 不是有效的類別定義，也無法產生新的實例。 可能是未完成，或尚未藉由呼叫 [PutClassWmi](putclasswmi.md)向 Windows 管理註冊。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` 為 `null`。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：： SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) 方法的呼叫。

`ptr` 必須是從 Windows 管理取得的類別定義。  (請注意，支援從實例產生實例，但是傳回的實例是空的。 ) 您接著使用這個類別定義來建立新的實例。 如果您想要將實例寫入 Windows 管理，則需要呼叫 [PutInstanceWmi](putinstancewmi.md) 函數。

中傳回的新物件 `ppNewClass` 會自動成為目前物件的子類別。 無法覆寫此行為。 無法建立子類別 (衍生類別) 的其他方法。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
