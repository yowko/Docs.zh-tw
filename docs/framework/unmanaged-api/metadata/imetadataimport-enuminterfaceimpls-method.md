---
title: IMetaDataImport::EnumInterfaceImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175495"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls 方法
枚舉指定`TypeDef`實現的所有介面。
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>參數  
 `phEnum`  
 [進出]指向枚舉器的指標。  
  
 `td`  
 [在]要枚舉其表示介面實現的 TypeDef 權杖的權杖。  
  
 `rImpls`  
 [出]用於存儲 MethodDef 權杖的陣列。  
  
 `cMax`  
 [在]`rImpls`陣列的最大長度。  
  
 `pcImpls`  
 [出]在 中`rImpls`返回的實際權杖數。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`已成功返回。|  
|`S_FALSE`|沒有要枚舉的 MethodDef 權杖。 在這種情況下，`pcImpls`設置為零。|  

## <a name="remarks"></a>備註

枚舉返回指定`mdInterfaceImpl``TypeDef`實現的每個介面的權杖集合。 介面權杖按指定介面（通過`DefineTypeDef`或`SetTypeDefProps`）的順序返回。 返回的`mdInterfaceImpl`權杖的屬性可以使用[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)查詢。
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
