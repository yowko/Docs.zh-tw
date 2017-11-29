---
title: "IMetaDataEmit::SetPropertyProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe79846b9fd576941c706b48a7aed0667c264a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps 方法
設定儲存在中繼資料屬性，在先前呼叫所定義的功能[DefineProperty 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `pr`  
 [in]若要變更屬性的語彙基元  
  
 `dwPropFlags`  
 [in]屬性旗標。  
  
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
 [in]其他方法與屬性相關聯的陣列。 終止這個陣列具有`mdTokenNil`語彙基元。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
