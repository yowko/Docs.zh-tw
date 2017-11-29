---
title: "IMetaDataEmit::GetTokenFromTypeSpec 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetTokenFromTypeSpec
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f83d1adb37691b525927eeb8a87b620fa3c7353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgettokenfromtypespec-method"></a>IMetaDataEmit::GetTokenFromTypeSpec 方法
取得具有指定的中繼資料簽章的類型中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvSig`  
 [in]正在定義的簽章。  
  
 `cbSig`  
 [in]中的位元組計數`pvSig`。  
  
 `ptypespec`  
 [out]`mdTypeSpec`指派的語彙基元。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
