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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c250a577f2ccdbbfefb35225b880c0e4317db36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448103"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty 方法
建立指定類型的屬性定義具有指定`get`和`set`方法存取子，並取得該屬性定義的語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `td`  
 [in]類別或介面定義屬性之語彙基元。  
  
 `szProperty`  
 [in]屬性的名稱。  
  
 `dwPropFlags`  
 [in]屬性的旗標。  
  
 `pvSig`  
 [in]屬性的簽章。  
  
 `cbSig`  
 [in]中的位元組計數`pvSig`。  
  
 `dwCPlusTypeFlag`  
 [in]屬性的預設值的類型。  
  
 `pValue`  
 [in]屬性的預設值。  
  
 `cchValue`  
 [in]中的字元 (Unicode) 的計數`pValue`。  
  
 `mdSetter`  
 [in]所設定的屬性值的方法。  
  
 `mdGetter`  
 [in]取得屬性值的方法。  
  
 `rmdOtherMethods[]`  
 [in]其他方法與屬性相關聯的陣列。 終止與陣列`mdTokenNil`。  
  
 `pmdProp`  
 [out]`mdProperty`指派的語彙基元。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
