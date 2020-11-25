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
ms.openlocfilehash: 27417c379411e242c48d6d9b0c99de833f7ede8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719264"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx 函式

取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。  
  
 此函數已被取代。 請改用 [ICLRStrongName：： StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>參數  

 `wszFilePath`  
 在可攜式可執行檔的路徑 ( .exe 或 .dll) 檔，以供要驗證的元件。  
  
 `fForceVerification`  
 [in] `true` 即使需要覆寫登錄設定，還是要執行驗證;否則為 `false` 。  
  
 `pfWasVerified`  
 [out] `true` 如果已驗證強式名稱簽章，否則為 `false` 。 `pfWasVerified``false`如果驗證因為登錄設定而成功，則也會設定為。  
  
## <a name="return-value"></a>傳回值  

 `true` 如果驗證成功，則為，否則為 `false` 。  
  
## <a name="remarks"></a>備註  

 `StrongNameSignatureVerificationEx` 提供類似于 [StrongNameSignatureVerification](strongnamesignatureverification-function.md) 函數的功能。 但是，的第二個輸入參數和的輸出參數 `StrongNameSignatureVerificationEx` 是類型， `BOOLEAN` 而不是 `DWORD` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureVerificationEx 方法](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification 方法](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
