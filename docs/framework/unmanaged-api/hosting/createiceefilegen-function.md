---
title: CreateICeeFileGen 函式
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e367ab3c966cea2d875b1de5b4244db5c4b813e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702219"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen 函式
會建立[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)物件。  
  
 此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ceeFileGen`  
 [out]新的位址指標`ICeeFileGen`物件。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準 COM 錯誤碼。  
  
## <a name="remarks"></a>備註  
 `ICeeFileGen`物件用來建立通用語言執行平台 (CLR) 可移植執行檔 (PE) 檔案。  
  
 呼叫[DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)函式終結`ICeeFileGen`物件時完成。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ICeeFileGen.h  
  
 **程式庫：** MSCorPE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
