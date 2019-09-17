---
title: StrongNameTokenFromAssembly 函式
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71058a1ff82335b2a341904805d06738e662c296
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798868"
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly 函式
從指定的組件檔案建立強式名稱權杖。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 在元件的可移植執行檔（PE）路徑。  
  
 `ppbStrongNameToken`  
 脫銷傳回的強式名稱 token。  
  
 `pcbStrongNameToken`  
 脫銷強式名稱 token 的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成時;否則為`false`。  
  
## <a name="remarks"></a>備註  
 強式名稱 token 是公用金鑰的縮寫格式。 Token 是從用來簽署元件的公開金鑰所建立的64位雜湊。 Token 是元件強式名稱的一部分，而且可以從元件中繼資料讀取。  
  
 建立權杖之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。  
  
 如果 `StrongNameTokenFromAssembly` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameTokenFromAssembly 方法](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx 方法](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
