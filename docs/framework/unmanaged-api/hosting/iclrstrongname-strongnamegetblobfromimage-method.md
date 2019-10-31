---
title: ICLRStrongName::StrongNameGetBlobFromImage 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: ad3b151165eb233bd3a4a78d8f4d612a696b7e93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135102"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a>ICLRStrongName::StrongNameGetBlobFromImage 方法
取得位於所指定記憶體位置之組件影像的二進位表示法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbBase`  
 在對應的組件資訊清單的記憶體位址。  
  
 `dwLength`  
 在影像在 `pbBase`的大小（以位元組為單位）。  
  
 `pbBlob`  
 在包含影像之二進位表示的緩衝區。  
  
 `pcbBlob`  
 [in、out]`pbBlob`的要求大小上限（以位元組為單位）。 傳回時，`pbBlob`的實際大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameGetBlob 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
