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
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798924"
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
 在表示執行驗證，即使需要覆寫登錄設定也一樣; `false`否則為。 `true`  
  
 `pfWasVerified`  
 脫銷如果已驗證強式名稱簽章，則為`false`，否則為。 `true` `pfWasVerified`如果驗證因為登錄`false`設定而成功，也會設定為。  
  
## <a name="return-value"></a>傳回值  
 `true`如果驗證成功，則為，否則為`false`。  
  
## <a name="remarks"></a>備註  
 `StrongNameSignatureVerificationEx`提供的功能類似于[StrongNameSignatureVerification](strongnamesignatureverification-function.md)函數。 不過，的第二個輸入參數和輸出參數`StrongNameSignatureVerificationEx`的類型`BOOLEAN`是，而`DWORD`不是。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureVerificationEx 方法](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification 方法](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
