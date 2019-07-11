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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72b95b634ffc352b7fad006e0ccd68e6e159dee9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779115"
---
# <a name="coinitializeee-function"></a>CoInitializeEE 函式
可確保 common language runtime 執行引擎會載入處理序。 在.NET Framework 4 中，此函式已被取代。 使用[iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `fFlags`  
 [in]其中一個[COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)列舉常數。  
  
## <a name="return-value"></a>傳回值  
 定義在 Winerror.h 和下表中的值，這個方法會傳回標準 COM 錯誤碼。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|執行引擎已順利載入。|  
|S_FALSE|已載入的執行引擎。|  
|E_FAIL|無法載入的執行引擎。|  
  
## <a name="remarks"></a>備註  
 如果先前尚未載入，這個方法會載入執行引擎。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
