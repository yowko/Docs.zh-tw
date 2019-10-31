---
title: ICLRStrongName::StrongNameSignatureVerificationEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: 3e4181cbd14674336133314acdcd6cdcf0c9ff6b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134936"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a>ICLRStrongName::StrongNameSignatureVerificationEx 方法
取得值，指出所提供路徑的組件資訊清單是否包含強式名稱簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。  
  
 `fForceVerification`  
 [in] `true` 執行驗證，即使需要覆寫登錄設定也一樣。否則，`false`。  
  
 `pfWasVerified`  
 [out] `true` 是否已驗證強式名稱簽章;否則，`false`。 如果驗證因為登錄設定而成功，`pfWasVerified` 也會設定為 `false`。  
  
## <a name="return-value"></a>傳回值  
 如果驗證成功，則 `S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。  
  
## <a name="remarks"></a>備註  
 [ICLRStrongName：： StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)方法提供的功能類似于[ICLRStrongName：： StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)方法。 不過， [ICLRStrongName：： StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)的第二個輸入參數和 output 參數是 `BOOLEAN` 類型，而不是 `DWORD`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameSignatureVerification 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
