---
title: IMetaDataEmit::SetPermissionSetProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: 1e6ee1f2f497ef30a5390e7afac55c54705248ed
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007802"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a>IMetaDataEmit::SetPermissionSetProps 方法
設定或更新先前呼叫 IMetaDataEmit 時所定義之許可權集合的中繼資料簽章功能[：:D efinepermissionset](imetadataemit-definepermissionset-method.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a>參數  
 `tk`  
 在表示要裝飾之物件的元資料標記。  
  
 `dwAction`  
 在[CorDeclSecurity](cordeclsecurity-enumeration.md)值，指定要使用的宣告式安全性類型。  
  
 `pvPermission`  
 在許可權 BLOB。  
  
 `cbPermission`  
 在的大小（以位元組為單位） `pvPermission` 。  
  
 `ppm`  
 脫銷`mdPermission`表示已更新之許可權的元資料標記。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
