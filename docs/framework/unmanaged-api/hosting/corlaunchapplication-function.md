---
title: CorLaunchApplication 函式
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
ms.openlocfilehash: e01698d2d8491b2496bb664c13dca97964cd1481
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136938"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication 函式
使用指定的資訊清單和其他應用程式資料，在指定的網路路徑啟動應用程式。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwClickOnceHost`  
 在[HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)列舉的值，指定正在啟動應用程式的主控制項類型。  
  
 `pwzAppFullName`  
 在正在啟動之應用程式的完整名稱。  
  
 `dwManifestPaths`  
 在應用程式的資訊清單路徑數目。  
  
 `ppwzManifestPaths`  
 在字串陣列，其中每個都指定要啟動之應用程式的資訊清單路徑。  
  
 `dwActivationData`  
 在正在啟動之應用程式的啟用資料項目數目。  
  
 `ppwzActivationData`  
 在字串陣列，其中每一個都是要啟動之應用程式的啟用資料項目。  
  
 `lpProcessInformation`  
 脫銷已載入應用程式之進程的相關資訊指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
