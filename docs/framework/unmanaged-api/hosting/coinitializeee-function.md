---
title: CoInitializeEE 函式
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9e90772ae8c3e6be5744fcccc9901123df871831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131934"
---
# <a name="coinitializeee-function"></a>CoInitializeEE 函式
確保 common language runtime 執行引擎已載入進程中。 此函式在 .NET Framework 4 中已被取代。 請改用[ICLRRuntimeHost：： Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `fFlags`  
 在其中一個[COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)列舉常數。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回 Winerror.h 中定義的標準 COM 錯誤碼，以及下表中的值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功載入執行引擎。|  
|S_FALSE|已載入執行引擎。|  
|E_FAIL|無法載入執行引擎。|  
  
## <a name="remarks"></a>備註  
 這個方法會載入執行引擎（如果先前尚未載入）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
