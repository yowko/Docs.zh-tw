---
title: IMetaDataError 介面
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 277b93267f0537c8e499a8d8f3b456c4396a975c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966345"
---
# <a name="imetadataerror-interface"></a>IMetaDataError 介面
提供回呼機制, 用於報告中繼資料合併期間的錯誤。  
  
> [!NOTE]
> `IMetaDataError`介面必須由用戶端執行。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[OnError 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|提供中繼資料合併期間發生之錯誤的通知。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 **LIBRARY:** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
