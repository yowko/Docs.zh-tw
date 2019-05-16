---
title: BlessIWbemServices 函式 （Unmanaged API 參考）
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb83bc3c0c7724dbcd3133465d4e7ad3a9eea3a9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636497"
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices 函式
表示使用者認證是否允許指定的存取[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)類別。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
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
[in]指標[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)權限所需的物件。

`strUser`\
[in]使用者名稱。

`strPassword`\
[in]與相關聯的密碼`strUser`。

`strAuthority`\
[in]使用者的網域名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`impLevel`\
[in]模擬等級。

`authnLevel`\
[in]授權層級。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WinError.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | 一或多個引數均為無效。 |
| `E_POINTER` | 0x80004003 | `pIWbemServices` 為 `null`。 | 
| `E_FAIL` | 0x80000008 | 發生未指定的錯誤。 |
| `E_OUTOFMEMORY` | 0x80000002 | 沒有足夠的記憶體可供執行作業。 | 
| `S_OK` | 0 | 函式呼叫成功。 | 

## <a name="requirements"></a>需求  

 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)
