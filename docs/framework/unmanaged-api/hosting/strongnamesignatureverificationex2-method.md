---
title: StrongNameSignatureVerificationEx2 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 641aaa42dca173de41afa099c91f78fecf691a7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689938"
---
# <a name="strongnamesignatureverificationex2-method"></a>StrongNameSignatureVerificationEx2 方法
驗證強式名稱的組件中，簽章，並提供實際的索引鍵與 ECMA 索引鍵的對應。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wszFilePath`  
 [in]可攜式可執行檔 （.exe 或.dll） 檔來進行驗證的組件的路徑。  
  
 `fForceVerification`  
 [in]`true`進行驗證，即使它是必要的登錄設定會覆寫，否則`false`。  
  
 `pbEcmaPublicKey`  
 [in]從實際的索引鍵的 ECMA 公開金鑰對應的指標，用來驗證。  
  
 `cbEcmaPublicKey`  
 [in]實際的 ECMA 公開金鑰長度。  
  
 `pfWasVerified`  
 [out]`true`強式名稱簽章是否已驗證，否則`false`。 這個參數也會設定為`false`若驗證成功因登錄設定。  
  
## <a name="return-value"></a>傳回值  
 `S_OK` 如果驗證成功;否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [StrongNameSignatureVerification 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
