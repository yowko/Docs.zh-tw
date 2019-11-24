---
title: IMetaDataFilter 介面
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: e8b15f478eb3b94b7cdcab3b69d54e7cc99be13b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440174"
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter 介面
提供標記和篩選中繼資料語彙基元的方法，以避免重複已採取的動作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IsTokenMarked 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|Gets a value indicating whether the specified metadata token has been processed.|  
|[MarkToken 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|Sets a value indicating that the specified metadata token has been processed.|  
|[UnmarkAll 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|Removes the processing marks from all the tokens in the current metadata scope.|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
