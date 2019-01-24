---
title: StrongNameSignatureVerificationEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9887a05236b213fb439e334cdf1455f8f445e7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671924"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx 函式
取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。  
  
 此函式已被取代。 使用[iclrstrongname:: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wszFilePath`  
 [in]可攜式可執行檔 （.exe 或.dll） 檔來進行驗證的組件的路徑。  
  
 `fForceVerification`  
 [in]`true`進行驗證，即使它是必要的登錄設定會覆寫，否則`false`。  
  
 `pfWasVerified`  
 [out]`true`強式名稱簽章是否已驗證，否則`false`。 `pfWasVerified` 也會設定為`false`若驗證成功因登錄設定。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果驗證成功;否則， `false`。  
  
## <a name="remarks"></a>備註  
 `StrongNameSignatureVerificationEx` 提供的功能類似於[StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)函式。 不過，第二個輸入參數和輸出參數`StrongNameSignatureVerificationEx`屬於類型`BOOLEAN`而不是`DWORD`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **程式庫：** 包含做為 mscoree.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [StrongNameSignatureVerificationEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
