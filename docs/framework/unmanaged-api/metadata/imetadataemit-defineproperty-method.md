---
title: IMetaDataEmit::DefineProperty 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: f11b374ed0ecbfc137c43fb641ae691237604691
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431529"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty 方法
使用指定的 `get` 和 `set` 方法存取子，為指定的類型建立屬性定義，並取得該屬性定義的 token。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineProperty (   
    [in]  mdTypeDef          td,   
    [in]  LPCWSTR            szProperty,   
    [in]  DWORD              dwPropFlags,   
    [in]  PCCOR_SIGNATURE    pvSig,   
    [in]  ULONG              cbSig,   
    [in]  DWORD              dwCPlusTypeFlag,   
    [in]  void const         *pValue,   
    [in]  ULONG              cchValue,   
    [in]  mdMethodDef        mdSetter,   
    [in]  mdMethodDef        mdGetter,   
    [in]  mdMethodDef        rmdOtherMethods[],   
    [out] mdProperty         *pmdProp   
);  
```  
  
## <a name="parameters"></a>參數  
 `td`  
 在要在其上定義屬性之類別或介面的 token。  
  
 `szProperty`  
 在屬性的名稱。  
  
 `dwPropFlags`  
 在屬性旗標。  
  
 `pvSig`  
 在屬性簽章。  
  
 `cbSig`  
 在`pvSig`中的位元組計數。  
  
 `dwCPlusTypeFlag`  
 在屬性的預設值類型。  
  
 `pValue`  
 在屬性的預設值。  
  
 `cchValue`  
 在`pValue`中的（Unicode）字元計數。  
  
 `mdSetter`  
 在設定屬性值的方法。  
  
 `mdGetter`  
 在取得屬性值的方法。  
  
 `rmdOtherMethods[]`  
 在與屬性相關聯之其他方法的陣列。 使用 `mdTokenNil`終止陣列。  
  
 `pmdProp`  
 脫銷指派的 `mdProperty` token。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
