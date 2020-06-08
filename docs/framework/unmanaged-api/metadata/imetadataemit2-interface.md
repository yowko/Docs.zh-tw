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
ms.openlocfilehash: 5a232f30da8812c6f3bd94647d74151312a8593b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493017"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 介面
延伸[IMetaDataEmit](imetadataemit-interface.md)介面，主要是為了提供使用泛型型別的能力。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DefineGenericParam 方法](imetadataemit2-definegenericparam-method.md)|建立泛型型別參數的定義，並取得該泛型型別參數的 token。|  
|[DefineMethodSpec 方法](imetadataemit2-definemethodspec-method.md)|建立方法的泛型實例，並取得定義的 token。|  
|[GetDeltaSaveSize 方法](imetadataemit2-getdeltasavesize-method.md)|取得值，表示為目前的「編輯後繼續」會話表示所需的資料大小差異。|  
|[ResetENCLog 方法](imetadataemit2-resetenclog-method.md)|重設 [編輯後繼續] 記錄並啟動新的會話。|  
|[SaveDelta 方法](imetadataemit2-savedelta-method.md)|將目前的「編輯後繼續」會話的變更儲存至指定的檔案。|  
|[SaveDeltaToMemory 方法](imetadataemit2-savedeltatomemory-method.md)|將目前的「編輯後繼續」會話的變更儲存至記憶體。|  
|[SaveDeltaToStream 方法](imetadataemit2-savedeltatostream-method.md)|將目前的「編輯後繼續」會話的變更儲存至指定的資料流程。|  
|[SetGenericParamProps 方法](imetadataemit2-setgenericparamprops-method.md)|針對指定之標記所參考的泛型參數定義，設定屬性值。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
