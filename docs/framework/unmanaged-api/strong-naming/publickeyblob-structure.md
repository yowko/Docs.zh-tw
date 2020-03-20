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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176951"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob 結構
以二進位格式表示公開金鑰/私密金鑰對的公開金鑰。  
  
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
|`SigAlgId`|公開金鑰的簽名演算法（類型`ALG_ID`，如 WinCrypt.h 中定義的）的識別碼。|  
|`HashAlgId`|公開金鑰的雜湊演算法（類型`ALG_ID`，在 WinCrypt.h 中定義）的識別碼。|  
|`cbPublicKey`|鍵的長度（以位元組為單位）。|  
|`PublicKey`|一個可變長度位元組陣列，包含 CryptoAPI 返回的格式中的鍵值。|  
  
## <a name="remarks"></a>備註  
 該`PublicKeyBlob`結構由[StrongNameGetPublicKey、](strongnamegetpublickey-function.md)[強式名稱簽名生成](strongnamesignaturegeneration-function.md)和其他強式名稱函數使用，以表示公開金鑰/私密金鑰對的公開金鑰。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 強式名稱.h  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameGetPublicKey 函式](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration 函式](strongnamesignaturegeneration-function.md)
