---
title: "GetPublicKeyToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetPublicKeyToken
api_location: alink.dll
api_type: COM
f1_keywords: GetPublicKeyToken
helpviewer_keywords: GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 230c98e85bd0aa3bd2f368965b6f7ac028e43df4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken 方法
擷取指定的 keyfile 或金鑰容器的公用金鑰語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `pszKeyFile`  
 金鑰的檔名。  
  
 `pszKeyContainer`  
 金鑰容器的名稱。  
  
 `pvPublicKeyToken`  
 儲存語彙基元的位址。  
  
 `pcbPublicKeyToken`  
 指定的大小，以位元組為單位，所指定的緩衝區`pvPublicKeyToken`。 傳回時，包含實際使用的位元組的數目。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h。  
  
## <a name="see-also"></a>請參閱  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
