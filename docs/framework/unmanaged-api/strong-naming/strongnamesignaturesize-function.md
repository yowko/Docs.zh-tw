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
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176886"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize 函式
傳回強式名稱簽章的大小。 `StrongNameSignatureSize`編譯器通常用於確定在創建延遲簽名程式集時檔中保留的空間。  
  
 此函數已被棄用。 改用[ICLR 強式名稱：：強式名稱簽名大小](../hosting/iclrstrongname-strongnamesignaturesize-method.md)方法。  
  
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
 [在][公共金鑰Blob](publickeyblob-structure.md)類型的結構，其中包含用於生成強式名稱簽名的金鑰組的公共部分。  
  
 `cbPublicKeyBlob`  
 [在]的大小（以位元組為單位）的大小`pbPublicKeyBlob`。  
  
 `pcbSize`  
 [在]存儲強式名稱簽名所需的位元組數。  
  
## <a name="return-value"></a>傳回值  
 `true`成功完成;否則， `false`.  
  
## <a name="remarks"></a>備註  
 如果`StrongNameSignatureSize`函數未成功完成，請調用[StrongNameErrorInfo 函數](strongnameerrorinfo-function.md)以檢索上次生成的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 強式名稱.h  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameSignatureSize 方法](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
