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
ms.openlocfilehash: 7a53b0a9cdcec33846f9d491e7d6567bcf9235b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication 函式
啟動指定的網路路徑，使用指定的資訊清單和其他應用程式資料在應用程式。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
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
  
#### <a name="parameters"></a>參數  
 `dwClickOnceHost`  
 [in]值為[HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)指定為啟動應用程式的主機類型的列舉。  
  
 `pwzAppFullName`  
 [in]正在啟動應用程式的完整名稱。  
  
 `dwManifestPaths`  
 [in]應用程式資訊清單路徑數目。  
  
 `ppwzManifestPaths`  
 [in]字串陣列，其中每個指定的路徑啟動應用程式資訊清單。  
  
 `dwActivationData`  
 [in]正在啟動應用程式啟用資料的項目數目。  
  
 `ppwzActivationData`  
 [in]字串陣列，其中每一個都是應用程式正在啟動的啟用資料項目。  
  
 `lpProcessInformation`  
 [out]程序中載入應用程式的相關資訊的指標。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
