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
ms.openlocfilehash: 7e0c689dad0c288e3af3a3d64ee1bba1c44053c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674524"
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
 在金鑰容器的名稱。 `wszKeyContainer` 必須是非空白字串。  
  
 `pbKeyBlob`  
 在二進位金鑰組。  
  
 `cbKeyBlob`  
 在的大小（以位元組為單位） `pbKeyBlob` 。  
  
## <a name="return-value"></a>傳回值  

 `S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>備註  

 使用 [ICLRStrongName：： StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) 方法來刪除金鑰容器。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StrongNameKeyDelete 方法](iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName 介面](iclrstrongname-interface.md)
