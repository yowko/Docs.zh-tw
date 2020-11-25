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
ms.openlocfilehash: 2c22e45ca3d33b0a81ff0ecd90bf7574c45676bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701844"
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter 介面

提供標記和篩選中繼資料語彙基元的方法，以避免重複已採取的動作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IsTokenMarked 方法](imetadatafilter-istokenmarked-method.md)|取得值，指出是否已處理指定的元資料標記。|  
|[MarkToken 方法](imetadatafilter-marktoken-method.md)|設定值，指出已處理指定的元資料標記。|  
|[UnmarkAll 方法](imetadatafilter-unmarkall-method.md)|從目前中繼資料範圍中的所有標記移除處理標記。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
