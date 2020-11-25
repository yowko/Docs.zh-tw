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
ms.openlocfilehash: 707e182e62f4a7b7b813e6b288c6825b0d3d2eab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731744"
---
# <a name="coinitializeee-function"></a>CoInitializeEE 函式

確保 common language runtime 執行引擎已載入至進程。 此函數在 .NET Framework 4 中已被取代。 請改用 [ICLRRuntimeHost：： Start](iclrruntimehost-start-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>參數  

 `fFlags`  
 在其中一個 [COINITIEE](../metadata/coinitiee-enumeration.md) 的列舉常數。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回 Winerror.h 中定義的標準 COM 錯誤碼，以及下表中的值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功載入執行引擎。|  
|S_FALSE|已載入執行引擎。|  
|E_FAIL|無法載入執行引擎。|  
  
## <a name="remarks"></a>備註  

 如果先前尚未載入執行引擎，這個方法會載入它。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
