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
ms.openlocfilehash: 11529ce896f265f2b200fa6e511d4b913e9147c8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008218"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken 方法
表示將會處理指定的元資料標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>參數  
 `tk`  
 在要處理的元資料標記。  
  
## <a name="remarks"></a>備註  
 一般而言，您想要在中繼資料範圍內處理權杖。 `MarkToken`方法會透過[IMetaDataEmit：： SetHandler](imetadataemit-sethandler-method.md)方法傳遞至中繼資料引擎。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
- [IHostFilter 介面](ihostfilter-interface.md)
