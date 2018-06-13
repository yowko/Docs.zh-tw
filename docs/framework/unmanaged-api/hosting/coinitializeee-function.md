---
title: CoInitializeEE 函式
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
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
ms.openlocfilehash: 8bbd25909e70826f8cd29076c1eb62a4da6779cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435397"
---
# <a name="coinitializeee-function"></a>CoInitializeEE 函式
確保 common language runtime 執行引擎載入處理序。 此函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 使用[iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fFlags`  
 [in]其中一個[COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)列舉常數。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準的 COM 錯誤碼定義於 Winerror.h，與下表中的值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|執行引擎已順利載入。|  
|S_FALSE|執行引擎已載入。|  
|E_FAIL|無法載入執行引擎。|  
  
## <a name="remarks"></a>備註  
 如果先前尚未載入這個方法會將載入的執行引擎。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
