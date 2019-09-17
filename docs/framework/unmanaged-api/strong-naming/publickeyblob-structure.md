---
title: PublicKeyBlob 結構
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e66196e2bd2cb326ca3f5badc67bcf8d81e5fc3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799169"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob 結構
代表公開/私密金鑰組的公開金鑰（二進位格式）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`SigAlgId`|公開金鑰的簽章演算法識別碼（類型`ALG_ID`為，如 WinCrypt 中所定義）。|  
|`HashAlgId`|公開金鑰的雜湊演算法識別碼（類型`ALG_ID`為，如 WinCrypt 中所定義）。|  
|`cbPublicKey`|金鑰的長度（以位元組為單位）。|  
|`PublicKey`|可變長度的位元組陣列，其中包含 CryptoAPI 所傳回之格式的索引鍵值。|  
  
## <a name="remarks"></a>備註  
 [StrongNameGetPublicKey](strongnamegetpublickey-function.md) `PublicKeyBlob`、[StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)和其他強式名稱函式會使用此結構來代表公開/私密金鑰組的公開金鑰。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetPublicKey 函式](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration 函式](strongnamesignaturegeneration-function.md)
