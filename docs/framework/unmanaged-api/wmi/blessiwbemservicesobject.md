---
title: BlessIWbemServicesObject 函式（非受控 API 參考）
description: BlessIWbemServicesObject 函數會指出使用者認證是否允許存取 IWbemServices 物件
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94c6f47e67cf22f189719a8a9f56e830ee90227c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798721"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject 函式
指出使用者認證是否允許存取指定的[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a>參數

`pIWbemServices`\
在WMI 服務物件的指標。

`strUser`\
在使用者名稱。

`strPassword`\
在與`strUser`相關聯的密碼。

`strAuthority`\
在使用者的功能變數名稱。 如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

`impLevel`\
在模擬層級。

`authnLevel`\
在授權層級。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*winerror.h*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | 一或多個引數無效。 |
| `E_POINTER` | 0x80004003 | `pIWbemServices` 為 `null`。 | 
| `E_FAIL` | 0x80000008 | 發生未指定的錯誤。 |
| `E_OUTOFMEMORY` | 0x80000002 | 記憶體不足，無法執行操作。 | 
| `S_OK` | 0 | 函式呼叫成功。 | 

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** WMINet_Utils.idl

 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
