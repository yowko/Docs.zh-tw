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
ms.openlocfilehash: 9ab44ce8f51620d83084d1dd16e98b2b310feb76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968943"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim 函式
載入包含在 .NET Framework 可轉散發套件中的指定 DLL 版本。  
  
 此函式在 .NET Framework 4 中已被取代。 請改用[ICLRRuntimeInfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法。  
  
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
 在以零結束的字串, 表示要從 .NET Framework 程式庫載入的 DLL 名稱。  
  
 `szVersion`  
 在以零結束的字串, 表示要載入之 DLL 的版本。 如果`szVersion`為 null, 則選取要載入的版本是最新版本的指定 DLL, 小於第4版。 也就是說, 如果`szVersion`為 null, 則會忽略等於或大於第4版的所有版本, 如果未安裝低於第4版的版本, 則無法載入 DLL。 這是為了確保 .NET Framework 4 的安裝不會影響既有的應用程式或元件。 請參閱 CLR team blog 中的進入[進程內 SxS 和遷移快速](https://go.microsoft.com/fwlink/?LinkId=200329)入門。  
  
 `pvReserved`  
 保留供未來使用。  
  
 `phModDll`  
 脫銷模組控制碼的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準元件物件模型 (COM) 錯誤碼 (如 Winerror.h 中所定義), 以及下列值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|CLR_E_SHIM_RUNTIMELOAD|載入`szDllName`需要載入 common language runtime (CLR), 而且無法載入必要的 CLR 版本。|  
  
## <a name="remarks"></a>備註  
 此函式是用來載入包含在 .NET Framework 可轉散發套件中的 Dll。 它不會載入使用者產生的 Dll。  
  
> [!NOTE]
> 從 .NET Framework 版本2.0 開始, 載入融合 .dll 會導致載入 CLR。 這是因為融合 .dll 中的函式現在是執行時間所提供的包裝函式。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
