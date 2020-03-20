---
title: CreateDebuggingInterfaceFromVersion 函式
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176444"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion 函式
根據指定的版本資訊創建[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件。  
  
 此功能在 .NET 框架 4 中已過時。 相反，要獲取通用語言運行時 （CLR） 2.0 的介面，請使用[ICLRRuntimeinfo：getInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法，並指定類識別碼CLSID_CLRDebuggingLegacy和介面識別碼IID_ICorDebug。 要獲取 CLR 4 或更高版本的介面，請調用[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函數，並指定類識別碼CLSID_CLRDebugging和介面識別碼IID_ICLRDebugging。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>參數  
 `iDebuggerVersion`  
 [在]`ICorDebug`調試器預期的版本。 有關有效值，請參閱[CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)枚舉。  
  
 `szDebuggeeVersion`  
 [在]與要調試的應用程式或進程關聯的通用語言執行階段版本。 有關檢索此值的資訊，請參閱[獲取從進程](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)獲取版本或[獲取請求執行階段版本](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)的方法。  
  
 `ppCordb`  
 [出]接收指向`ICorDebug`物件的指標的位置。  
  
## <a name="return-value"></a>傳回值  
 此方法返回 WinError.h 檔中定義的標準 COM 錯誤代碼以及以下值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szDebuggeeVersion`或`ppCordb`為 null，或者版本字串不正確。|  
  
## <a name="remarks"></a>備註  
 參數`szDebuggeeVersion`映射到相應的 MSCorDbi.dll 版本。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
