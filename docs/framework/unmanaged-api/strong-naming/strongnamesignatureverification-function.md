---
title: StrongNameSignatureVerification 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3cd2a123e495b4bf19168e86932c866c91e980f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751626"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification 函式
取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。  
  
 此函式已被取代。 使用[iclrstrongname:: Strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 [in]可攜式可執行檔 （.dll 或.exe） 檔來確認組件路徑。  
  
 `dwInFlags`  
 [in]若要修改的驗證行為的旗標。 支援下列值：  
  
- `SN_INFLAG_FORCE_VER` (0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。  
  
- `SN_INFLAG_INSTALL` (0x00000002)-指定驗證資訊清單的第一次。  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004)-指定快取可讓具有系統管理權限的使用者存取。  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008)-指定的組件都是僅供目前的使用者存取。  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010)-指定快取會提供任何保證的存取限制。  
  
- `SN_INFLAG_RUNTIME` (0x80000000)-保留給內部偵錯。  
  
 `pdwOutFlags`  
 [out]旗標，指出是否已驗證的強式名稱簽章。 支援下列值：  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-此值設為`false`，指定驗證成功，因為登錄設定。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果驗證成功;否則， `false`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureVerification 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
