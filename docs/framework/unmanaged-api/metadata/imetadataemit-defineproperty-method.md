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
ms.openlocfilehash: 479cb25ad8e1c263d3539a4203ac5bea781eb931
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009370"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty 方法
使用指定的和方法存取子，為指定的類型建立屬性定義 `get` `set` ，並取得該屬性定義的 token。  
  
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
 在中的位元組計數 `pvSig` 。  
  
 `dwCPlusTypeFlag`  
 在屬性的預設值類型。  
  
 `pValue`  
 在屬性的預設值。  
  
 `cchValue`  
 在中的（Unicode）字元計數 `pValue` 。  
  
 `mdSetter`  
 在設定屬性值的方法。  
  
 `mdGetter`  
 在取得屬性值的方法。  
  
 `rmdOtherMethods[]`  
 在與屬性相關聯之其他方法的陣列。 使用終止陣列 `mdTokenNil` 。  
  
 `pmdProp`  
 脫銷`mdProperty`指派的 token。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
