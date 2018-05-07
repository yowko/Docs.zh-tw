---
title: IMetaDataEmit::SetParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61688ed5201a1bb6721c4db70b380c7b8373c2e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetparamprops-method"></a>IMetaDataEmit::SetParamProps 方法
設定或變更在先前呼叫所定義的方法參數的功能[imetadataemit:: Defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a>參數  
 `pd`  
 [in]目標參數的語彙基元。  
  
 `szName`  
 [in]以 Unicode 參數的名稱。  
  
 `dwParamFlags`  
 [in]參數的旗標。  
  
 `dwCPlusTypeFlag`  
 [in]ELEMENT_TYPE_ * 常數的值。  
  
 `pValue`  
 [in]參數的常值。  
  
 `cchValue`  
 [in]以 (Unicode) 字元為單位的大小`pValue`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
