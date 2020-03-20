---
title: 生成實例函數（非託管 API 引用）
description: SpawnInstance 函數創建類的新實例。
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
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176717"
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
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`lFlags`  
[in] 保留。 此參數必須為 0。

`ppNewInstance`  
[出]接收指向類新實例的指標。 如果發生錯誤，則不會返回新物件，並且`ppNewInstance`未修改。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0 x80041020 | `ptr`不是有效的類定義，不能生成新實例。 要麼不完整，要麼沒有通過調用[PutClassWmi](putclasswmi.md)在 Windows 管理中註冊。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` 為 `null`。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數將調用包起來到[IWbem ClassObject：：spawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)方法。

`ptr`必須是從 Windows 管理獲取的類定義。 （請注意，支援從實例生成實例，但返回的實例為空。然後，使用此類定義創建新實例。 如果要將實例寫入 Windows 管理，則需要調用[PutInstanceWmi](putinstancewmi.md)函數。

返回`ppNewClass`的新物件將自動成為當前物件的子類。 無法重寫此行為。 沒有其他方法可以創建子類（派生類）。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
