---
title: QualifierSet_Delete 函式 （Unmanaged API 參考）
description: QualifierSet_Delete 函式會刪除限定詞名稱。
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
ms.openlocfilehash: 956abe8ddf8075b7b8f8c057db0aa7187982e1d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782603"
---
# <a name="qualifiersetdelete-function"></a>QualifierSet_Delete 函式
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
[in]未使用此參數。

`ptr`   
[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。

`wszName`   
[in]若要刪除限定詞的名稱。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 |           `wszName` 參數無效。 |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | 刪除這個限定詞是不合法的。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 找不到指定的限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | 本機覆寫已經刪除，原始的辨識符號，從父物件已重新開始範圍。 |

## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)方法。

限定詞傳播規則，因為特定的辨識符號可能已繼承自另一個物件和只是覆寫目前的類別或執行個體中。 在此情況下，`QualifierSet_Delete`方法重設為其原始的繼承值的限定詞。 函式在此情況下會傳回狀態碼`WBEM_S_RESET_TO_DEFAULT`。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)
