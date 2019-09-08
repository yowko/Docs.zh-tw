---
title: QualifierSet_Delete 函式（非受控 API 參考）
description: QualifierSet_Delete 函數會依名稱刪除限定詞。
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bc26a16650a5beecc17898e0421e79536713deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798332"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete 函式
依名稱刪除指定的限定詞。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
在未使用此參數。

`ptr`   
在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。

`wszName`   
在要刪除的限定詞名稱。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` 參數無效。 |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | 刪除這個限定詞是不合法的。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 找不到指定的限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | 已刪除本機覆寫，且父物件的原始辨識符號已恢復範圍。 |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemQualifierSet：:D 刪除](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)方法的呼叫。

由於限定詞傳播規則的緣故，特定的辨識符號可能已經繼承自另一個物件，而且只會在目前的類別或實例中覆寫。 在此情況下， `QualifierSet_Delete`方法會將限定詞重設為其原始的繼承值。 在此情況下，函式會傳回`WBEM_S_RESET_TO_DEFAULT`狀態碼。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
