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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c997ab107ba3ceb7773bc9235b9c9dcd4d97df8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231444"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication 函式
啟動指定的網路路徑，使用指定的資訊清單和其他應用程式資料的應用程式。  
  
 此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]值為[HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)列舉，指定正在啟動應用程式的主控件的型別。  
  
 `pwzAppFullName`  
 [in]正在啟動應用程式的完整名稱。  
  
 `dwManifestPaths`  
 [in]應用程式資訊清單路徑數目。  
  
 `ppwzManifestPaths`  
 [in]字串陣列，每一個都會指定要啟動之應用程式資訊清單的路徑。  
  
 `dwActivationData`  
 [in]正在啟動之應用程式啟用資料的項目數目。  
  
 `ppwzActivationData`  
 [in]字串陣列，每個都是要啟動之應用程式的啟用資料的項目。  
  
 `lpProcessInformation`  
 [out]程序中載入應用程式的相關資訊的指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
