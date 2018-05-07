---
title: BlessIWbemServices 函式 （Unmanaged API 參考）
description: BlessIWbemServices 函式指示使用者認證是否允許存取 IWbemServices 類別。
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
ms.openlocfilehash: 59cb20f7ccfbd0b8f9d6026c9805468613818130
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="blessiwbemservices-function"></a>BlessIWbemServices 函式
表示使用者認證是否允許存取指定[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)類別。   
  
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

`pIWbemServices`  
[in]指標[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)權限所需的物件。

`strUser`  
[in]使用者名稱。

`strPassword`  
[in]與相關聯的密碼`strUser`。

`strAuthority` [in]使用者的網域名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`impLevel` [in]模擬等級。

`authnLevel` [in]授權層級。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WinError.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | 一或多個引數均為無效。 |
| `E_POINTER` | 0x80004003 | `pIWbemServices` 為 `null`。 | 
| `E_FAIL` | 0x80000008 | 發生意外的錯誤。 |
| `E_OUTOFMEMORY` | 0x80000002 | 記憶體不足，無法使用執行作業。 | 
| `S_OK` | 0 | 函式呼叫成功。 | 

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
