---
title: StrongNameKeyGen 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f062f47790136e8cd39c6751b7c75eef660c2b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799146"
---
# <a name="strongnamekeygen-function"></a>StrongNameKeyGen 函式
建立將供強式名稱使用的新公開/私密金鑰組。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszKeyContainer`  
 在要求的金鑰容器名稱。 `wszKeyContainer`必須是非空白字串，否則為 null，以產生暫存名稱。  
  
 `dwFlags`  
 在指定是否要保留註冊的金鑰。 支援下列值：  
  
- 0x00000000-在為`wszKeyContainer` null 時使用，以產生暫存金鑰容器名稱。  
  
- 0x00000001 （`SN_LEAVE_KEY`）-指定應將金鑰保留為已註冊。  
  
 `ppbKeyBlob`  
 脫銷傳回的公開/私密金鑰組。  
  
 `pcbKeyBlob`  
 脫銷的大小（以位元組為單位`ppbKeyBlob`）。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成時;否則為`false`。  
  
## <a name="remarks"></a>備註  
 `StrongNameKeyGen`函式會建立1024位金鑰。 在取得金鑰之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。  
  
 如果 `StrongNameKeyGen` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameKeyGen 方法](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [StrongNameKeyGenEx 方法](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
