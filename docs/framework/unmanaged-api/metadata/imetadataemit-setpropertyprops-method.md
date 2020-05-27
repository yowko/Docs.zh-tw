---
title: IMetaDataEmit::SetPropertyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007776"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps 方法
針對先前呼叫[DefineProperty 方法](imetadataemit-defineproperty-method.md)所定義的屬性，設定儲存在中繼資料中的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a>參數  
 `pr`  
 在要變更之屬性的標記  
  
 `dwPropFlags`  
 在屬性旗標。  
  
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
 在與屬性相關聯之其他方法的陣列。 使用權杖終止此陣列 `mdTokenNil` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
