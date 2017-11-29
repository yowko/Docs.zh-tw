---
title: "IMetaDataFilter::MarkToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter.MarkToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 608d7aa87103c5144997bfa1feb69a88b5fb1ffe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafiltermarktoken-method"></a>IMetaDataFilter::MarkToken 方法
設定值，指出指定的中繼資料語彙基元已經處理。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `tk`  
 [in]要標記為已處理的語彙基元。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataFilter 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
