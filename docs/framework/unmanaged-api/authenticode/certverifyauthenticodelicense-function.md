---
title: CertVerifyAuthenticodeLicense 函式
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06f69bf867b565edbab06dadb32e5377357e91f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617688"
---
# <a name="certverifyauthenticodelicense-function"></a>CertVerifyAuthenticodeLicense 函式
驗證 Authenticode XrML 授權的有效性。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>參數  
 `pLicenseBlob`  
 [in] 要驗證的 Authenticode XrML 授權。  
  
 請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。  
  
 `dwFlags`  
 [in] 選用。 下列值的組合：  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 [out] 接收簽署者的資訊。 若授權未經簽署，`dwError` 會設為 TRUST_E_NOSIGNATURE。 釋放資源使用的呼叫者必須負責[CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)之後使用的函式。  
  
 請參閱[AXL_AUTHENTICODE_SIGNER_INFO 結構](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)。  
  
 `pTimestamperInfo`  
 [out] 接收時間戳記設定者的資訊 (如有提供)。 若授權未設定時間戳記，`dwError` 會設為 TRUST_E_NOSIGNATURE。 釋放資源使用的呼叫者必須負責[CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)之後使用的函式。  
  
 請參閱[AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)。  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [GetHashFromHandle 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
