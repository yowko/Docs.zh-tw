---
title: QualifierSet_Delete功能（非託管 API 引用）
description: QualifierSet_Delete函數按名稱刪除限定詞。
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
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174897"
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
[在]此參數未使用。

`ptr`[在]指向[IWbem 限定詞集實例的](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標。

`wszName`[在]要刪除的限定詞的名稱。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` 參數無效。 |
|`WBEM_E_INVALID_OPERATION` | 0 x80041016 | 刪除此限定詞是非法的。 |
|`WBEM_E_NOT_FOUND` | 0 x80041002 | 未找到指定的限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_RESET_TO_DEFAULT` | 0 x40002 | 本地重寫已被刪除，父物件的原始限定詞已恢復作用域。 |

## <a name="remarks"></a>備註

此函數包裝對[IWbem 限定詞集：:Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)方法的調用。

由於限定詞傳播規則，特定限定詞可能從另一個物件繼承，並且只是在當前類或實例中重寫。 在這種情況下，`QualifierSet_Delete`該方法將限定詞重置為其原始繼承的值。 在這種情況下，函數返回狀態碼`WBEM_S_RESET_TO_DEFAULT`。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
