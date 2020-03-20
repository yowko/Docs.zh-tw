---
title: ICLRStrongName::StrongNameSignatureSize 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: e789996af3aedd17251fc52cde52a336f65053ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176340"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a>ICLRStrongName::StrongNameSignatureSize 方法
傳回強式名稱簽章的大小。 編譯器通常使用此方法來確定在創建延遲簽名程式集時要在檔中保留多少空間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a>參數  
 `pbPublicKeyBlob`  
 [在][公共金鑰Blob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)類型的結構，其中包含用於生成強式名稱簽名的金鑰組的公共部分。  
  
 `cbPublicKeyBlob`  
 [在]的大小（以位元組為單位）的大小`pbPublicKeyBlob`。  
  
 `pcbSize`  
 [在]存儲強式名稱簽名所需的位元組數。  
  
## <a name="return-value"></a>傳回值  
 `S_OK`如果方法成功完成;如果方法成功完成;否則，指示失敗的 HRESULT 值（請參閱清單[的常用 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MetaHost.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
