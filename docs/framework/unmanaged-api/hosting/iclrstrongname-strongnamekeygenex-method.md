---
title: ICLRStrongName::StrongNameKeyGenEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: 9ba50616b25f9c7c592f19947c82a890ae6b5a4a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671677"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a>ICLRStrongName::StrongNameKeyGenEx 方法

使用指定的金鑰大小產生新的公開/私密金鑰組，以供強式名稱使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
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
  
 `dwKeySize`  
 在要求的金鑰大小（以位為單位）。  
  
 `ppbKeyBlob`  
 擴展傳回的公開/私密金鑰組。  
  
 `pcbKeyBlob`  
 擴展的大小（以位元組為單位） `ppbKeyBlob` 。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>備註  

 .NET Framework 版本1.0 和1.1 需要 `dwKeySize` 1024 位來簽署具有強式名稱的元件; 2.0 版新增了針對2048位金鑰支援的功能。  
  
 在抓取金鑰之後，您應該呼叫 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法來釋放已配置的記憶體。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameKeyGen 方法](iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
