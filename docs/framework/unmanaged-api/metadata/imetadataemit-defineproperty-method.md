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
ms.openlocfilehash: d2a4a15126f34666a58021a59e9e193685b15a49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719485"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty 方法

使用指定的和方法存取子，針對指定的型別建立屬性定義， `get` `set` 並取得該屬性定義的標記。  
  
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
 在要在其上定義屬性之類別或介面的標記。  
  
 `szProperty`  
 在屬性的名稱。  
  
 `dwPropFlags`  
 在屬性旗標。  
  
 `pvSig`  
 在屬性簽章。  
  
 `cbSig`  
 在中的位元組計數 `pvSig` 。  
  
 `dwCPlusTypeFlag`  
 在屬性預設值的型別。  
  
 `pValue`  
 在屬性的預設值。  
  
 `cchValue`  
 在 (的 Unicode) 字元計數 `pValue` 。  
  
 `mdSetter`  
 在設定屬性值的方法。  
  
 `mdGetter`  
 在取得屬性值的方法。  
  
 `rmdOtherMethods[]`  
 在與屬性相關聯之其他方法的陣列。 使用來終止陣列 `mdTokenNil` 。  
  
 `pmdProp`  
 擴展 `mdProperty` 指派的權杖。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
