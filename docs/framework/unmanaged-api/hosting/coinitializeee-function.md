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
ms.openlocfilehash: 57508a2df3a49c39d25347f2a3038442c37278da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616758"
---
# <a name="coinitializeee-function"></a>CoInitializeEE 函式
確保 common language runtime 執行引擎已載入進程中。 此函式在 .NET Framework 4 中已被取代。 請改用[ICLRRuntimeHost：： Start](iclrruntimehost-start-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `fFlags`  
 在其中一個[COINITIEE](../metadata/coinitiee-enumeration.md)列舉常數。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回 Winerror.h 中定義的標準 COM 錯誤碼，以及下表中的值。  
  
|傳回碼|說明|  
|-----------------|-----------------|  
|S_OK|已成功載入執行引擎。|  
|S_FALSE|已載入執行引擎。|  
|E_FAIL|無法載入執行引擎。|  
  
## <a name="remarks"></a>備註  
 這個方法會載入執行引擎（如果先前尚未載入）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
