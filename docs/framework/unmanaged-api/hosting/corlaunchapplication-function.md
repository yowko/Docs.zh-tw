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
ms.openlocfilehash: ca427439f03d92b20e7714b9724d90b240e9cecb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704067"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication 函式

使用指定的資訊清單和其他應用程式資料，在指定的網路路徑上啟動應用程式。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
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
 在 [HOST_TYPE](host-type-enumeration.md) 列舉值，這個值會指定正在啟動應用程式的主控制項類型。  
  
 `pwzAppFullName`  
 在即將啟動之應用程式的完整名稱。  
  
 `dwManifestPaths`  
 在應用程式的資訊清單路徑數目。  
  
 `ppwzManifestPaths`  
 在字串的陣列，每個字串都指定要啟動之應用程式的資訊清單路徑。  
  
 `dwActivationData`  
 在即將啟動之應用程式的啟用資料項目數目。  
  
 `ppwzActivationData`  
 在字串的陣列，每個字串都是正在啟動之應用程式的啟用資料項目。  
  
 `lpProcessInformation`  
 擴展已載入應用程式之進程的相關資訊指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
