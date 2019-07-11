---
title: LoadLibraryShim 函式
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03bc5584d24efa790989f93426251f9f38e65904
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768530"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim 函式
載入的 DLL 隨附於.NET Framework 可轉散發套件中指定的版本。  
  
 此函式已被取代，在.NET Framework 4。 使用[iclrruntimeinfo:: Loadlibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>參數  
 `szDllName`  
 [in]零結尾的字串，表示要載入從.NET Framework 程式庫 DLL 的名稱。  
  
 `szVersion`  
 [in]零結尾的字串，表示要載入的 dll 版本。 如果`szVersion`是 null，選取 載入為指定的 DLL 是小於第 4 版的最新版本的版本。 如果，亦即忽略所有版本等於或大於第 4 版`szVersion`為 null，但如果已安裝任何版本小於第 4 版，無法載入 DLL。 這是為了確保，.NET Framework 4 的安裝不會影響現有的應用程式或元件。 請參閱文章[In-proc SxS 並快速開始進行移轉](https://go.microsoft.com/fwlink/?LinkId=200329)CLR 小組的部落格。  
  
 `pvReserved`  
 保留供未來使用。  
  
 `phModDll`  
 [out]模組的控制代碼指標。  
  
## <a name="return-value"></a>傳回值  
 中所定義 WinError.h，除了下列的值，這個方法會傳回標準的元件物件模型 (COM) 錯誤代碼。  
  
|傳回碼|說明|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|CLR_E_SHIM_RUNTIMELOAD|正在載入`szDllName`需要的載入 common language runtime (CLR)，以及必要的 CLR 版本無法載入。|  
  
## <a name="remarks"></a>備註  
 此函式用來載入 Dll 隨附於.NET Framework 可轉散發套件。 它不會載入使用者產生的 Dll。  
  
> [!NOTE]
>  從.NET Framework 2.0 版開始，載入 Fusion.dll 造成載入 CLR。 這是因為 Fusion.dll 中的函式現在是包裝函式執行階段所提供的實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
