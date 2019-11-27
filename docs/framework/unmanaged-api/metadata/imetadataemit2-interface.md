---
title: IMetaDataEmit2 介面
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: 7ceae6f7713ab0eb1feff550838325df0ea52de2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447910"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 介面
延伸[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面，主要是為了提供使用泛型型別的能力。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DefineGenericParam 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|建立泛型型別參數的定義，並取得該泛型型別參數的 token。|  
|[DefineMethodSpec 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|建立方法的泛型實例，並取得定義的 token。|  
|[GetDeltaSaveSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|取得值，表示為目前的「編輯後繼續」會話表示所需的資料大小差異。|  
|[ResetENCLog 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|重設 [編輯後繼續] 記錄並啟動新的會話。|  
|[SaveDelta 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|將目前的「編輯後繼續」會話的變更儲存至指定的檔案。|  
|[SaveDeltaToMemory 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|將目前的「編輯後繼續」會話的變更儲存至記憶體。|  
|[SaveDeltaToStream 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|將目前的「編輯後繼續」會話的變更儲存至指定的資料流程。|  
|[SetGenericParamProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|針對指定之標記所參考的泛型參數定義，設定屬性值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
