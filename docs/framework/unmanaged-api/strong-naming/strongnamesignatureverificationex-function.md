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
ms.openlocfilehash: ca428d680df1710d8e74441d9945d4c3545b0482
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121151"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx 函式
取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)方法。  
  
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
 在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。  
  
 `fForceVerification`  
 [in] `true` 執行驗證，即使需要覆寫登錄設定也一樣。否則，`false`。  
  
 `pfWasVerified`  
 [out] `true` 是否已驗證強式名稱簽章;否則，`false`。 如果驗證因為登錄設定而成功，`pfWasVerified` 也會設定為 `false`。  
  
## <a name="return-value"></a>傳回值  
 如果驗證成功，則 `true`;否則，`false`。  
  
## <a name="remarks"></a>備註  
 `StrongNameSignatureVerificationEx` 提供類似[StrongNameSignatureVerification](strongnamesignatureverification-function.md)函數的功能。 不過，`StrongNameSignatureVerificationEx` 的第二個輸入參數和輸出參數是 `BOOLEAN` 類型，而不是 `DWORD`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結**庫：** 包含為 mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameSignatureVerificationEx 方法](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification 方法](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
