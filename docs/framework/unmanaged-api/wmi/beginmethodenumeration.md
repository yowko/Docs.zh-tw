---
title: 開始方法枚舉函數（非託管 API 引用）
description: BeginMethodEee）函數開始枚舉物件的方法
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 876f5810fffab7fa98cd4d46715e13569ab95f6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175040"
---
# <a name="beginmethodenumeration-function"></a>BeginMethodEnumeration 函式
開始枚舉可用於物件的方法。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`lEnumFlags`  
[在]所有方法的零 （0） 或指定枚舉範圍的標誌。 以下標誌在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 將枚舉限制為在類本身中定義的方法。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 將枚舉限制為從基類繼承的屬性。 |

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags`是非零，不是指定的標誌之一。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbemClassObject 的調用：：開始方法枚舉](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration)方法。

僅當當前物件是類定義時，才支援此方法調用。 方法操作從指向實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標中不可用。 對於[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的給定實例，方法的枚舉順序保證為不變。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
