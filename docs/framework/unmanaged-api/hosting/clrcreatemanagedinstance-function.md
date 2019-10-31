---
title: ClrCreateManagedInstance 函式
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 4e672030ae83b57da6f9ab66630513d79f28b8f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131994"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance 函式
建立指定之 managed 類型的實例。  
  
 此函式在 .NET Framework 4 中已被取代。 使用 COM 啟動來建立 managed 類型的實例，或使用裝載（請參閱[在 .NET Framework 4 和4.5 中新增的 CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `pTypeName`  
 在所要求之實例類型名稱的指標。  
  
 `riid`  
 在所要求之實例類型的 `IID`。  
  
 `ppObject`  
 脫銷呼叫端所要求之 managed 型別的實例指標。  
  
## <a name="remarks"></a>備註  
 通用語言執行平臺應該已經載入進程中。 例如，您可以在呼叫 `ClrCreateManagedInstance` 函式之前，使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函數的呼叫來載入它。 如果未載入執行時間，`ClrCreateManagedInstance` 會先嘗試載入執行時間的 v v1.0.3705。 如果失敗，則會嘗試載入最新版本的執行時間。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
