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
ms.openlocfilehash: f8448de17ad974bc77021a7880b7d8576c69ae75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750908"
---
# <a name="imetadataemitsetparamprops-method"></a>IMetaDataEmit::SetParamProps 方法
設定或變更已由先前呼叫的方法參數的功能[imetadataemit:: Defineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a>參數  
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
 [in]\(Unicode\) 字元的大小`pValue`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
