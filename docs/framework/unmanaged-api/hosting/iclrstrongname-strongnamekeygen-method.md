---
title: ICLRStrongName::StrongNameKeyGen 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: 42a9fc1a05e97bbd893f0a2e77087e6524ad844f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674537"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen 方法

建立將供強式名稱使用的新公開/私密金鑰組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>參數  

 `wszKeyContainer`  
 在要求的金鑰容器名稱。 `wszKeyContainer` 必須為非空白字串或 null，才能產生暫存名稱。  
  
 `dwFlags`  
 在值，指定是否要保留註冊的金鑰。 支援下列值：  
  
- 0x00000000-當 `wszKeyContainer` 為 null 時，用來產生暫存金鑰容器名稱。  
  
- 0x00000001 (`SN_LEAVE_KEY`) -指定應該將金鑰保持在註冊。  
  
 `ppbKeyBlob`  
 擴展傳回的公開/私密金鑰組。  
  
 `pcbKeyBlob`  
 擴展的大小（以位元組為單位） `ppbKeyBlob` 。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>備註  

 [ICLRStrongName：： StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md)方法會建立1024位的金鑰。 在抓取金鑰之後，您應該呼叫 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法來釋放已配置的記憶體。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameKeyGenEx 方法](iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
