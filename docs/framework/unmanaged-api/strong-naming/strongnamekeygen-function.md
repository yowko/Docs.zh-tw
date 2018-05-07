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
ms.openlocfilehash: 5fce08434cb8864350fd333dcfcaa388a8031c09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamekeygen-function"></a>StrongNameKeyGen 函式
建立新公用/私密金鑰組的強式名稱使用。  
  
 此函式已被取代。 使用[iclrstrongname:: Strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wszKeyContainer`  
 [in]要求的金鑰容器名稱。 `wszKeyContainer` 必須是非空白字串，或 null 以產生暫時的名稱。  
  
 `dwFlags`  
 [in]指定是否要保留已註冊的鍵。 支援下列值：  
  
-   0x00000000-時使用`wszKeyContainer`以產生暫時的金鑰容器名稱為 null。  
  
-   0x00000001 (`SN_LEAVE_KEY`)-指定應該向左登錄機碼。  
  
 `ppbKeyBlob`  
 [out]傳回的 public/private 金鑰組。  
  
 `pcbKeyBlob`  
 [out]大小，以位元組為單位的`ppbKeyBlob`。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果成功地完成。否則， `false`。  
  
## <a name="remarks"></a>備註  
 `StrongNameKeyGen`函式會建立為 1024年位元金鑰。 擷取索引鍵之後，您應該呼叫[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式釋放配置的記憶體。  
  
 如果`StrongNameKeyGen`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** StrongName.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [StrongNameKeyGen 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [StrongNameKeyGenEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
