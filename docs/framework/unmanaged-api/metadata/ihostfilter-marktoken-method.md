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
ms.openlocfilehash: 52375486eb9d7780a51808dedc5f876587efb115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
 [in]要處理的中繼資料語彙基元。  
  
## <a name="remarks"></a>備註  
 您通常會想要如果在中繼資料範圍內處理的語彙基元。 `MarkToken`方法傳遞至中繼資料引擎透過[imetadataemit:: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IHostFilter 介面](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
