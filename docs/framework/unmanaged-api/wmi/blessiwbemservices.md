---
title: 'BlessIWbemServices 函式 (非受控 API 參考) '
description: BlessIWbemServices 函式會指出使用者認證是否允許存取 IWbemServices 類別。
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 43ef617ee754c9dcd661b31abba6b17434563c22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708149"
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices 函式

指出使用者認證是否允許存取指定的 [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) 類別。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>參數

`pIWbemServices`\
在需要許可權的 [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) 物件指標。

`strUser`\
在使用者名稱。

`strPassword`\
在與相關聯的密碼 `strUser` 。

`strAuthority`\
在使用者的功能變數名稱。 如需詳細資訊，請參閱 [ConnectServerWmi](connectserverwmi.md) 函數。

`impLevel`\
在模擬等級。

`authnLevel`\
在授權層級。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *winerror.h .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | 一或多個引數無效。 |
| `E_POINTER` | 且顯示0x80004003 | `pIWbemServices` 為 `null`。 |
| `E_FAIL` | 0x80000008 | 發生未指定的錯誤。 |
| `E_OUTOFMEMORY` | 0x80000002 | 記憶體不足，無法執行此作業。 |
| `S_OK` | 0 | 函式呼叫成功。 |

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
