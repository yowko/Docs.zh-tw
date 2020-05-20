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
ms.openlocfilehash: 0e1395229b67c4054df62935375a4136edf63078
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616485"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion 函式
根據指定的版本資訊建立[ICorDebug](../debugging/icordebug-interface.md)物件。  
  
 此函式在 .NET Framework 4 中已過時。 相反地，若要取得 common language runtime （CLR）2.0 的介面，請使用[ICLRRuntimeInfo：： GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法，並指定 CLSID_CLRDebuggingLegacy 的類別識別碼和 IID_ICorDebug 的介面識別碼。 若要取得 CLR 4 或更新版本的介面，請呼叫[CLRCreateInstance](clrcreateinstance-function.md)函式，並指定 CLSID_CLRDebugging 的類別識別碼和 IID_ICLRDebugging 的介面識別碼。  
  
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
 在`ICorDebug`偵錯工具所需的版本。 如需有效的值，請參閱[CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md)列舉。  
  
 `szDebuggeeVersion`  
 在與要進行調試的應用程式或進程相關聯的 common language runtime 版本。 如需有關抓取此值的詳細資訊，請參閱[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)或[GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md)方法。  
  
 `ppCordb`  
 脫銷接收物件指標的位置 `ICorDebug` 。  
  
## <a name="return-value"></a>傳回值  
 除了下列值之外，這個方法會傳回 Winerror.h 檔案中定義的標準 COM 錯誤碼。  
  
|傳回碼|說明|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`szDebuggeeVersion`或 `ppCordb` 為 null，或版本字串不正確。|  
  
## <a name="remarks"></a>備註  
 `szDebuggeeVersion`參數會對應至相對應的 mscordbi.dll 版本。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
