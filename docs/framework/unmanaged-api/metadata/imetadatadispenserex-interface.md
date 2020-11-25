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
ms.openlocfilehash: 60d321c1a87a5da433437c9d4587fa9f8947acf4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713375"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx 介面

擴充 [IMetaDataDispenser 介面](imetadatadispenser-interface.md) 介面，以提供控制中繼資料 api 在目前中繼資料範圍上運作方式的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FindAssembly 方法](imetadatadispenserex-findassembly-method.md)|這個方法尚未實作。 如果呼叫，則會傳回 E_NOTIMPL。|  
|[FindAssemblyModule 方法](imetadatadispenserex-findassemblymodule-method.md)|這個方法尚未實作。 如果呼叫，則會傳回 E_NOTIMPL。|  
|[GetCORSystemDirectory 方法](imetadatadispenserex-getcorsystemdirectory-method.md)|取得保存目前 common language runtime (CLR) 的目錄。 只有跨進程偵錯工具才能使用此方法。 如果從另一個元件呼叫，則會傳回 E_NOTIMPL。|  
|[GetOption 方法](imetadatadispenserex-getoption-method.md)|取得目前中繼資料範圍之指定選項的值。 選項會控制如何處理目前中繼資料範圍的呼叫。|  
|[OpenScopeOnITypeInfo 方法](imetadatadispenserex-openscopeonitypeinfo-method.md)|這個方法尚未實作。 如果呼叫，則會傳回 E_NOTIMPL。|  
|[SetOption 方法](imetadatadispenserex-setoption-method.md)|將指定的選項設定為目前中繼資料範圍的指定值。 選項會控制如何處理目前中繼資料範圍的呼叫。|  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
- [IMetaDataDispenser 介面](imetadatadispenser-interface.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
