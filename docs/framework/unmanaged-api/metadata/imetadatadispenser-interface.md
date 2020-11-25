---
title: IMetaDataDispenser 介面
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: c798aeba46adf91a8c13f8143c00f02173a0bb52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726102"
---
# <a name="imetadatadispenser-interface"></a>IMetaDataDispenser 介面

提供方法來建立新的中繼資料範圍，或開啟現有的範圍。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DefineScope 方法](imetadatadispenser-definescope-method.md)|在記憶體中建立新的區域，您可以在其中建立新的中繼資料。|  
|[OpenScope 方法](imetadatadispenser-openscope-method.md)|開啟現有的磁片上的檔案，並將其中繼資料對應到記憶體。|  
|[OpenScopeOnMemory 方法](imetadatadispenser-openscopeonmemory-method.md)|開啟包含現有中繼資料的記憶體區域。 也就是說，這個方法會開啟指定的記憶體區域，其中現有的資料會被視為中繼資料。|  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataDispenserEx 介面](imetadatadispenserex-interface.md)
- [中繼資料介面](metadata-interfaces.md)
