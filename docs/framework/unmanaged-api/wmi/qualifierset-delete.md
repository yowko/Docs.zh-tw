---
title: 'QualifierSet_Delete 函式 (非受控 API 參考) '
description: QualifierSet_Delete 函數會依名稱刪除辨識符號。
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
ms.openlocfilehash: 2000de77903c3dabb43116fa1700b4ed393aeb5a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721149"
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
在此參數未使用。

`ptr` 在 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 實例的指標。

`wszName` 在要刪除的辨識符號名稱。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` 參數無效。 |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | 刪除此限定詞不合法。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 找不到指定的限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | 已刪除本機覆寫，且父物件的原始辨識符號已恢復範圍。 |

## <a name="remarks"></a>備註

此函數會包裝對 [IWbemQualifierSet：:D elete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) 方法的呼叫。

由於限定詞傳播規則，特定限定詞可能已繼承自另一個物件，而只會在目前的類別或實例中覆寫。 在此情況下， `QualifierSet_Delete` 方法會將限定詞重設為其原始的繼承值。 在此情況下，函式會傳回狀態碼 `WBEM_S_RESET_TO_DEFAULT` 。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
