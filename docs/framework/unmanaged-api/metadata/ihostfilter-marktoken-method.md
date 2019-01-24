---
title: IHostFilter::MarkToken 方法
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4a1761f088732cf19d55f42d66288bb281885f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589447"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken 方法
表示將處理指定的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `tk`  
 [in]處理中繼資料語彙基元。  
  
## <a name="remarks"></a>備註  
 一般而言，您會想在中繼資料範圍內無法處理的語彙基元。 `MarkToken`方法傳遞至中繼資料引擎，透過[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IHostFilter 介面](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
