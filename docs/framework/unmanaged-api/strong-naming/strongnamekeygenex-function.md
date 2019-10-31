---
title: StrongNameKeyGenEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: 63ddd90f3a8090853d10f03052915d10e1503ea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125207"
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx 函式
產生具有指定金鑰大小的新公開/私密金鑰組，以供強式名稱使用。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszKeyContainer`  
 在要求的金鑰容器名稱。 `wszKeyContainer` 必須是非空白字串，或為 null 以產生暫存名稱。  
  
 `dwFlags`  
 在指定是否要保留註冊的金鑰。 支援下列值：  
  
- 0x00000000-在 `wszKeyContainer` 為 null 時用來產生暫存金鑰容器名稱。  
  
- 0x00000001 （`SN_LEAVE_KEY`）-指定應將金鑰保留為已註冊。  
  
 `dwKeySize`  
 在要求的金鑰大小（以位為單位）。  
  
 `ppbKeyBlob`  
 脫銷傳回的公開/私密金鑰組。  
  
 `pcbKeyBlob`  
 脫銷`ppbKeyBlob`的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 成功完成時 `true`;否則，`false`。  
  
## <a name="remarks"></a>備註  
 .NET Framework 版本1.0 和1.1 需要1024位的 `dwKeySize`，才能以強式名稱簽署元件;2.0 版新增了2048位金鑰的支援。  
  
 在取得金鑰之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。  
  
 如果 `StrongNameKeyGenEx` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameKeyGenEx 方法](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen 方法](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
