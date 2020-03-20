---
title: 刪除方法函數（非託管 API 引用）
description: DeleteMethod 函數從 CIM 類定義中刪除指定的方法。
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4059555d74c0b0f151332ddcf9faedecf238e795
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174988"
---
# <a name="deletemethod-function"></a>DeleteMethod 函式
從 CIM 類定義中刪除指定的方法。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`wszName`  
[在]要從類表中刪除的方法的名稱。 `wszName`必須是指向有效`LPCWSTR`指標的 指標。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | 0 x80041002 | 指定的方法不存在。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 記憶體不足，無法完成此作業。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函數包裝對[IWbemClassObject：:Delete 方法的](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod)調用。

對於指向 CIM 實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標，不支援方法刪除。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
