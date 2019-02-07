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
ms.openlocfilehash: 5f66d91434fd92ff80bb17e04bf38bb0b631e819
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825494"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary 方法
取得程式庫提供者回呼介面，可讓 common language runtime (CLR) 版本特定偵錯程式庫尋找並載入需求。  
  
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
 [in]COFF 檔案標頭的 PE 檔中儲存的日期時間戳記。  
  
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
 `ProvideLibrary` 可讓偵錯工具提供所需的偵錯特定的 CLR 檔案，例如 mscordbi.dll 和 mscordacwks.dll 的模組。 模組控制代碼必須保持有效，直到呼叫[iclrdebugging:: Canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)方法表示它們可能會釋出，此時必須負責呼叫者釋放控制代碼。  
  
 偵錯工具可以使用任何可用的方式，來找出或購買的偵錯的模組。  
  
> [!IMPORTANT]
>  這項功能可讓 API 呼叫端，以提供包含可執行檔，並可能是惡意的程式碼的模組。 為了安全起見，呼叫端不應該使用`ProvideLibrary`散發不願意執行本身的任何程式碼。  
>   
>  如果已發行的文件庫，例如 mscordbi.dll 或 mscordacwks.dll 中, 探索到嚴重的安全性問題可辨識不正確的版本檔案的修補填充碼。 填充碼然後發出要求的修補檔案的版本，並拒絕不正確的版本，如果提供以回應任何要求。 這可能是只有當使用者有新的版本，填充碼修正的項目。 未更新的版本仍易受攻擊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
