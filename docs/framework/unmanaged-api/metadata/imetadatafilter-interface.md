---
title: "IMetaDataFilter 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter
helpviewer_keywords: IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7c0afbb9be9af3ffe69ddfcac85b70de53a391ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter 介面
提供標記和篩選中繼資料語彙基元的方法，以避免重複已採取的動作。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[IsTokenMarked 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|取得值，指出是否已經處理指定的中繼資料語彙基元。|  
|[MarkToken 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|設定值，指出指定的中繼資料語彙基元已經處理。|  
|[UnmarkAll 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|移除目前的中繼資料範圍內的所有權杖處理標記。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
