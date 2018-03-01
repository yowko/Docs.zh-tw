---
title: "_AxlPublicKeyBlobToPublicKeyToken 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c9dfd42d0908032ed9a652f6f4f5736ba775ce8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>_AxlPublicKeyBlobToPublicKeyToken 函式
從 CSP PUBLICKEYBLOB 格式運算強式名稱公開金鑰語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCspPublicKeyBlob`  
 [in] CSP 公開金鑰 Blob。  
  
 `ppwszPublicKeyHash`  
 [out] WCHAR * 的指標，可接收十六進位編碼公開金鑰雜湊。  
  
## <a name="return-value"></a>傳回值  
 若函式成功則傳回 `S_OK`：反之則傳回 `S_FALSE`。  
  
## <a name="see-also"></a>請參閱  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
