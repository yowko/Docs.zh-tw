---
title: StrongNameSignatureSize 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a8856790b655f071df704879a247169f456ae2f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130880"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize 函式
傳回強式名稱簽章的大小。 在建立延遲簽署的元件時，編譯器通常會使用 `StrongNameSignatureSize` 來決定要在檔案中保留多少空間。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a>參數  
 `pbPublicKeyBlob`  
 在[PublicKeyBlob](publickeyblob-structure.md)類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。  
  
 `cbPublicKeyBlob`  
 在`pbPublicKeyBlob`的大小（以位元組為單位）。  
  
 `pcbSize`  
 在儲存強式名稱簽章所需的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 成功完成時 `true`;否則，`false`。  
  
## <a name="remarks"></a>備註  
 如果 `StrongNameSignatureSize` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameSignatureSize 方法](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
