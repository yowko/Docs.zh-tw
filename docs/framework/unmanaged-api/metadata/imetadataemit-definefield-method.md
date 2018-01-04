---
title: "IMetaDataEmit::DefineField 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2c4b5604c3daec78744eb8902a30750571b9f82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField 方法
建立欄位的定義，與指定的中繼資料簽章，並取得該欄位定義的語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a>參數  
 `td`  
 [in]`mdTypeDef`權杖封入類別或介面。  
  
 `szName`  
 [in]以 Unicode 欄位名稱。  
  
 `dwFieldFlags`  
 [in]欄位屬性。 這是位元遮罩`CorFieldAttr`值。  
  
 `pvSigBlob`  
 [in]欄位簽章為 BLOB。  
  
 `cbSigBlob`  
 [in]中的位元組計數`pvSigBlob`。  
  
 `dwCPlusTypeFlage`  
 [in]`ELEMENT_TYPE_`  *\** 常數的值。 這是`CorElementType`值。 如果未定義欄位的常數值，使用`ELEMENT_TYPE_END`。  
  
 `pValue`  
 [in]欄位的常值。  
  
 `cchValue`  
 [in]以 (Unicode) 字元為單位的大小`pValue`。  
  
 `pmd`  
 [out]`mdFieldDef`指派的語彙基元。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
