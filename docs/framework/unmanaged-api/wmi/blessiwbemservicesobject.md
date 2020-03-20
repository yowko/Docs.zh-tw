---
title: 祝福IWbem服務物件功能（非託管 API 引用）
description: 祝福IWbem服務物件功能指示使用者憑據是否允許訪問 IWbem 服務物件
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
ms.openlocfilehash: fd822f78d29ad3a75fb5e57dd7c23b7049d445b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175027"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject 函式
指示使用者憑據是否允許訪問指定的[IWbem 服務](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件。

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
[在]指向 WMI 服務物件的指標。

`strUser`\
[在]使用者名。

`strPassword`\
[在]與`strUser`關聯的密碼。

`strAuthority`\
[在]使用者的功能變數名稱。 有關詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。

`impLevel`\
[在]類比級別。

`authnLevel`\
[在]授權級別。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WinError.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | 一個或多個參數無效。 |
| `E_POINTER` | 0x80004003 | `pIWbemServices` 為 `null`。 |
| `E_FAIL` | 0x80000008 | 發生未指定的錯誤。 |
| `E_OUTOFMEMORY` | 0x80000002 | 可用記憶體不足以執行操作。 |
| `S_OK` | 0 | 函式呼叫成功。 |

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標題：** WMINet_Utils.idl

 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
