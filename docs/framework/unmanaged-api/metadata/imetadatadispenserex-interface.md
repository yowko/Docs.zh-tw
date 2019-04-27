---
title: IMetaDataDispenserEx 介面
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992598"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx 介面
擴充[IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)介面，以提供的功能，來控制中繼資料 Api 如何處理目前的中繼資料範圍。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FindAssembly 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|這個方法尚未實作。 如果呼叫，它會傳回 E_NOTIMPL。|  
|[FindAssemblyModule 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|這個方法尚未實作。 如果呼叫，它會傳回 E_NOTIMPL。|  
|[GetCORSystemDirectory 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|取得儲存目前的 common language runtime (CLR) 的目錄。 這個方法是僅支援使用由跨處理序偵錯工具。 如果從另一個元件呼叫，它會傳回 E_NOTIMPL。|  
|[GetOption 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|取得目前的中繼資料範圍的指定選項的值。 此選項會控制如何處理目前的中繼資料範圍的呼叫。|  
|[OpenScopeOnITypeInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|這個方法尚未實作。 如果呼叫，它會傳回 E_NOTIMPL。|  
|[SetOption 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|將指定的選項，設定目前的中繼資料範圍的指定值。 此選項會控制如何處理目前的中繼資料範圍的呼叫。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
