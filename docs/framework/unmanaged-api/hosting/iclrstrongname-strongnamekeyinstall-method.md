---
title: ICLRStrongName::StrongNameKeyInstall 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a2badf8f164abd1bbb8892ec5db28f7cf39f5c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775662"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a>ICLRStrongName::StrongNameKeyInstall 方法
將公開/私密金鑰組匯入到容器中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszKeyContainer`  
 [in]金鑰容器的名稱。 `wszKeyContainer` 必須是非空白字串。  
  
 `pbKeyBlob`  
 [in]二進位金鑰組。  
  
 `cbKeyBlob`  
 [in]大小，以位元組為單位的`pbKeyBlob`。  
  
## <a name="return-value"></a>傳回值  
 `S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。  
  
## <a name="remarks"></a>備註  
 使用[iclrstrongname:: Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)方法來刪除金鑰容器。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameKeyDelete 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
