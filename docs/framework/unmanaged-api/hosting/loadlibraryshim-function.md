---
title: "LoadLibraryShim 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LoadLibraryShim
helpviewer_keywords: LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c56f5a3576c505fd7b7d514e3f2d038e7f8f3ecc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim 函式
載入 DLL 隨附於.NET Framework 可轉散發套件中的指定的版本。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 使用[iclrruntimeinfo:: Loadlibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szDllName`  
 [in]零結尾的字串，表示要從.NET Framework 程式庫載入 DLL 的名稱。  
  
 `szVersion`  
 [in]零結尾的字串，表示要載入的 dll 版本。 如果`szVersion`是 null，選取為載入指定之 dll 小於第 4 版的最新版本的版本。 如果，亦即，忽略所有的版本等於或大於第 4 版`szVersion`為 null，但如果安裝沒有版本小於第 4 版，則無法載入 DLL。 這是為了確保安裝[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]不會影響現有的應用程式或元件。 請參閱文章[同處理序 SxS 和移轉快速入門](http://go.microsoft.com/fwlink/?LinkId=200329)CLR team 部落格中。  
  
 `pvReserved`  
 保留供未來使用。  
  
 `phModDll`  
 [out]模組的控制代碼指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準的元件物件模型 (COM) 的錯誤代碼，除了下列的值定義了 WinError.h 中。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|CLR_E_SHIM_RUNTIMELOAD|載入`szDllName`需要的載入，無法載入 common language runtime (CLR)，以及必要的 CLR 版本。|  
  
## <a name="remarks"></a>備註  
 此函式用來載入 Dll 隨附的.NET Framework 可轉散發套件。 它不會載入使用者產生的 Dll。  
  
> [!NOTE]
>  從.NET Framework 2.0 版開始，載入 Fusion.dll 會造成載入 CLR。 這是因為 Fusion.dll 中的函式現在是包裝函式的實作所提供的執行階段。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
