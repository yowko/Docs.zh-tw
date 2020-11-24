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
ms.openlocfilehash: 4c3e0953d71020ba62ee4ab68aa9e21ea3f0f521
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675031"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a>IMetaDataEmit::SetPermissionSetProps 方法

設定或更新由先前呼叫 [IMetaDataEmit：:D efinepermissionset](imetadataemit-definepermissionset-method.md)所定義之許可權集合的中繼資料簽章功能。  
  
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
 在元資料標記，代表要裝飾的物件。  
  
 `dwAction`  
 在 [CorDeclSecurity](cordeclsecurity-enumeration.md) 值，指定要使用的宣告式安全性類型。  
  
 `pvPermission`  
 在許可權 BLOB。  
  
 `cbPermission`  
 在的大小（以位元組為單位） `pvPermission` 。  
  
 `ppm`  
 擴展 `mdPermission` 代表更新之許可權的元資料標記。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
