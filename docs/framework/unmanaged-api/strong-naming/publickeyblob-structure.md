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
ms.openlocfilehash: 42cd3cc22fbbb8eb3d5ac44544fce36650b6461f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705926"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob 結構

以二進位格式表示公開/私密金鑰組的公開金鑰。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`SigAlgId`|型別之簽章演算法 (的識別碼 `ALG_ID` ，如公開金鑰) WinCrypt 中所定義。|  
|`HashAlgId`|雜湊演算法 (的識別碼 `ALG_ID` ，如公開金鑰的 WinCrypt) 中所定義。|  
|`cbPublicKey`|金鑰的長度（以位元組為單位）。|  
|`PublicKey`|可變長度位元組陣列，其中包含 CryptoAPI 傳回之格式的索引鍵值。|  
  
## <a name="remarks"></a>備註  

 `PublicKeyBlob` [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)和其他強式名稱函數會使用此結構來代表公開/私密金鑰組的公開金鑰。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetPublicKey 函式](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration 函式](strongnamesignaturegeneration-function.md)
