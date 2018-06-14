---
title: ICLRDebuggingLibraryProvider::ProvideLibrary 方法
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0644258eb1622f388f55d0657c8922079fe4dc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407225"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary 方法
取得程式庫提供者回呼介面，common language runtime (CLR) 版本特定偵錯程式庫找到並載入需求。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a>參數  
 `pwszFilename`  
 [in]所要求的模組名稱。  
  
 `dwTimestamp`  
 [in]日期時間戳記儲存在 PE 檔的 COFF 檔案標頭。  
  
 `pLibraryProvider`  
 [in]`SizeOfImage` COFF 選用的檔案標頭的 PE 檔中儲存的欄位。  
  
 `hModule`  
 [out]要求的模組控制代碼。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 `ProvideLibrary` 可讓偵錯工具，以提供所需的偵錯特定的 CLR 檔案，例如 mscordbi.dll 與 mscordacwks.dll 的模組。 模組控制代碼必須維持有效，直到呼叫[iclrdebugging:: Canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)方法表示可能會釋放，此時必須負責呼叫者釋放控制代碼。  
  
 偵錯工具可以使用任何可用的方法來找出或採購偵錯模組。  
  
> [!IMPORTANT]
>  這項功能可讓應用程式開發介面呼叫者提供包含可執行檔，且可能是惡意程式碼模組。 基於安全性考量，呼叫端不應該使用`ProvideLibrary`散發不願意執行本身的任何程式碼。  
>   
>  如果已發行的程式庫，例如 mscordbi.dll 或 mscordacwks.dll，發現嚴重的安全性問題以辨識不正確的檔案版本修補填充碼。 填充碼然後發出要求的修補檔案的版本，並拒絕不正確的版本，如果回應任何要求中提供。 只有當使用者已經修補至新版的填充碼，也可能會發生。 未更新的版本仍會有弱點。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
