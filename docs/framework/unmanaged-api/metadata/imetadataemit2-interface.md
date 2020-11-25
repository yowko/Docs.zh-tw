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
ms.openlocfilehash: b8ad159dace734c343297b256092162f17ab829b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726479"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 介面

擴充 [IMetaDataEmit](imetadataemit-interface.md) 介面，主要是為了提供使用泛型型別的能力。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DefineGenericParam 方法](imetadataemit2-definegenericparam-method.md)|建立泛型型別參數的定義，並取得該泛型型別參數的標記。|  
|[DefineMethodSpec 方法](imetadataemit2-definemethodspec-method.md)|建立方法的泛型實例，並取得定義的標記。|  
|[GetDeltaSaveSize 方法](imetadataemit2-getdeltasavesize-method.md)|取得值，指出表示目前編輯後繼續會話變更所需的資料大小差異。|  
|[ResetENCLog 方法](imetadataemit2-resetenclog-method.md)|重設編輯後繼續記錄，並啟動新的會話。|  
|[SaveDelta 方法](imetadataemit2-savedelta-method.md)|將目前的編輯後繼續會話的變更儲存至指定的檔案。|  
|[SaveDeltaToMemory 方法](imetadataemit2-savedeltatomemory-method.md)|將目前的編輯後繼續會話的變更儲存至記憶體。|  
|[SaveDeltaToStream 方法](imetadataemit2-savedeltatostream-method.md)|將目前的編輯後繼續會話的變更儲存至指定的資料流程。|  
|[SetGenericParamProps 方法](imetadataemit2-setgenericparamprops-method.md)|設定指定之標記所參考之泛型參數定義的屬性值。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](metadata-interfaces.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
