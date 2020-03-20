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
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176535"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance 函式
創建指定託管類型的實例。  
  
 此功能已在 .NET 框架 4 中棄用。 使用 COM 啟動創建託管類型的實例，或使用託管（請參閱[在 .NET 框架 4 和 4.5 中添加的 CLR 託管介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)）。  
  
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
 [在]指向要請求的實例類型的名稱的指標。  
  
 `riid`  
 [在]要`IID`請求的實例類型的 。  
  
 `ppObject`  
 [出]指向調用方請求的託管類型的實例的指標。  
  
## <a name="remarks"></a>備註  
 公共語言運行時應已載入到進程中。 例如，在調用`ClrCreateManagedInstance`函數之前，可以使用對[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函數的調用來載入它。 如果未載入運行時，`ClrCreateManagedInstance`則首先嘗試載入運行時的 v1.0.3705。 如果失敗，它將嘗試載入最新版本的運行時。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
