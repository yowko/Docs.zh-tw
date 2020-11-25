---
title: IMetaDataConverter 介面
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: 74804cdc9dc04c3ede5cc26a6310dbb3948cd78a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729482"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter 介面

提供將類型程式庫對應至它們的中繼資料簽章，以及從一個轉換到另一個的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo 方法](imetadataconverter-getmetadatafromtypeinfo-method.md)|取得 [IMetaDataImport](imetadataimport-interface.md) 實例的指標，該實例表示指定實例所參考之類型程式庫的中繼資料簽章 `ITypeInfo` 。|  
|[GetMetaDataFromTypeLib 方法](imetadataconverter-getmetadatafromtypelib-method.md)|取得 `IMetaDataImport` 實例的指標，該實例表示指定實例所代表之類型程式庫的中繼資料簽章 `ITypeLib` 。|  
|[GetTypeLibFromMetaData 方法](imetadataconverter-gettypelibfrommetadata-method.md)|取得 `ITypeLib` 實例的指標，該實例表示具有指定模組和程式庫名稱的類型程式庫。|  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
